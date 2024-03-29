# The OCDB command line client (ocdb-cli) and Python API

Automation and easy access is important. The OCDB database system does,
therefore, offer a command line interface as well as a Python API for accessing
as well as managing submissions and users.

Both options offer the same functions. If you just want to apply one or more of these functions,
the command line interface (CLI) will suit your needs. Otherwise, use the OCDB API in Python scripts
to integrate OCDB API functions together with other Python tasks.


## Installation

It is possible to install the CLI and API via conda:

```bash
conda install -c ocdb -c conda-forge ocdb-client
```

Once that is done, you can test whether it is running by

cli:
```bash
ocdb-cli


Usage: ocdb-cli [OPTIONS] COMMAND [ARGS]...

  EUMETSAT Ocean Color In-Situ Database Client.

Options:
  --version       Show the version and exit.
  --server <url>  OC-DB Server URL.
  --help          Show this message and exit.

Commands:
  conf     Configuration management.
  ds       Dataset management.
  lic      Show license and exit.
  sbm      Submission management.
  sbmfile  Submission management.
  user     User management.
```

## Configure

In order to access the database you need to configure the REST API server address.
The default address to be used is ```https://ocdb.eumetsat.int```, i. e.:


### cli:
```bash
# Check whether the server url for the ocdb-cli is configured:
ocdb-cli conf 

https://ocdb.eumetsat.int

ocdb-cli conf server_url [some url]
```

### python:
```python
from ocdb.api.OCDBApi import new_api

api = new_api()

api.config

#Out[11]: {'server_url': 'https://ocdb.eumetsat.int'}

api.set_config_param('server_url','[some server url]')

```

## Search Database with find_datasets()

After login (see chapter "User Management" below), the method 'find_datasets' allows querying
the Database for multiple dataset characteristics, using different keywords:

- __expr__: looks for any files containing any of the words passed. Also, Lucene syntax can be used (See below for more details)
- __region__: looks for files containing measurements collected in the polygon defined by specified coordinates (format: "[West],[South],[East],[North]")
- __start_time__: looks for any files containing measurement collected later than the selected date (format: "20160701")
- __end_time__: looks for any files containing measurement collected earlier than the selected date (format: "20190701")
- __wdepth__: looks for any files containing measurements collected within the defined range of water (bottom) depth (format:"[[min_depth],[max_depth]]")
- __mtype__: filters radiometric data depending on wavelength option. Could be 'all', 'multispectral' or 'hyperspectral'
- __shallow__: set to 'yes' to include also measurements indicated as done in shallow waters by the PIs (Default is 'no')
- __pmode__: can be set either to 'contains' (to filter results based on selected pgroup or variables), or to 'same_cruise' (to include measurements from cruise during which __all__ the selected groups/variables were acquired), or to 'do_not_filter' (to not filter results at all) 
- __pgroup__: looks for files containing only certain geophysical variable types. Refer to [Search the OCDB using the GUI](ocdb-search.md) chapter for the complete list
- __pname__: looks for files containing only the specified variables. A complete list of queryable variables are available [OCDB standard field names and units](ocdb-standard-field-unit.md)
- __status__: set to 'PUBLISHED' to get only public available data or to 'PROCESSED' to get both public and not published data (available only for admin users and data owners) 
- __submission_id__: looks for data submitted below the specified submission label
- __geojson__: (Default is True)
- __user_id__: look for data submitted by the specified user (by username)

The result is a dictionary containing information and whole dataset related to the file containing the measurement the satisfied the search criteria.
Dictionary keys are: 

- *locations*: geometries representing the spatial extent of each dataset (point or rectangle)
- *total_count*: number of datasets returned by the query
- *datasets*: information about dataset files and the submissions they belong to
- *query*: query parameterization
- *dataset_ids*: ids of the returned datasets

The syntax to search for SEABASS datasets via the command line interface is:

cli syntax: 
```bash
ocdb-cli ds find --query [keyword]=[value or comma-separated list of values]
```

cli sample: 
```bash
ocdb-cli ds find --query region=50,45,51,46
ocdb-cli ds find --query start_time=2021-01-01 --query end_time=2021-12-31
```

The Python method find_dataset( ... ) can be used as follows:

```python
def find_datasets(ctx: WsContext,
                  expr: str = None,    # Lucene syntax can be used here!
                  region: List[float] = None,    # comma-separated list of floats
                  mtype: str = None,             # e. g. 'scan', 'above_water', ...
                  wlmode: str = None,            # Not implemented yet
                  shallow: str = 'no',           # as defined in metadata header "/data_use_warning= ..." 
                  pmode: str = 'contains',       # e. g. "same cruise", "contains"       
                  pgroup: List[str] = None,      # For details refer to: https://ocdb.readthedocs.io/en/latest/ocdb-search.html#product-groups
                  status: str = None,            # Not implemented yet
                  submission_id: str = None,     # equal to submission label as defined at submission
                  pname: List[str] = None,       # for wavelength-dependent parameters, e. g. Lsky412, please use LUcene syntax
                  geojson: bool = False,         # boolean, default is false
                  offset: int = 1,               # used by web user interface for paging
                  user_id: str = None,           # used by web user interface
                  count: int = 1000)             # used by web user interface for paging, default = 1000
```

Python samples:
```python
data = api.find_datasets(region='50,45,51,46')
data['datasets']

  [{'id': '5d97112af9305e0001c6d6fc', 'path': 'LOG/IOPstudy/DS3', 'filename': 'DS3_IOPstudy.csv'}]
data = api.find_datasets(end_time='2021-12-31')
```

## Search Database with Lucene syntax

The first example below attempts to find data files that include the name *"Astrid"* in the investigators meta field.

cli:
```bash
ocdb-cli ds find --expr "investigators: *Astrid*"
```

results in the following output:

```bash
{
  "locations": {},
  "total_count": 4,
  "datasets": [
    {
      "id": "5d2433e81f59e20001aaae74",
      "path": "AWI/SO/SO235/archive/Bracher_2019_SO235_db.txt"
    },
    ...
```

python:
```python
api.find_datasets(expr="investigators=*Astrid*")
```

results in the following output:

```python
{
  "locations": {},
  "total_count": 4 ,
  "datasets": [
    {
      "id": "5d2433e81f59e20001aaae74",
      "path": "AWI/SO/SO235/archive/Bracher_2019_SO235_db.txt"
    },
    ...
```

A complete and up-to-date list of the fields that can be queried is available [Search the OCDB using the GUI](ocdb-search.md)

## Get Datasets

The search engine returns a list of datasets. In order to retrieve the actual data, dataset IDs obtained through the previous step, using cli ds find function and api find_datasets method, should be used. A dataset ID can be used to get actual data as in the example below:

cli:
```bash
ocdb-cli ds get --id 5d971154f9305e0001c6d700
```

python:
```python
api.get_dataset(dataset_id='5d971154f9305e0001c6d700', fmt='pandas')
```

results in the following output:

```python
	      date	    time	     lat	    lon	depth	  ...	 tot_chl_a
0     20140723	12:30:00	-19.9743	57.4493	    0	     	  0.05280
1	  20140723	14:00:00	-19.7216	57.6288	    0		      0.04767
2	  20140723	17:00:00	-19.2121	57.9908	    0		      0.05028
3	  20140723	20:00:00	-18.7211	58.3397	    0             0.04490
4	  20140723	23:00:00	-18.2994	58.7023	    0		      0.07901
:
```

## User Management

Commands:
- __add__     Add a user (see below)
- __delete__  Delete user <username> (see below)
- __get__     Get user <username> (see below)
- __list__    List all user (ocdb-cli user list)
- __login__   Login a user (see below)
- __logout__  Log out current user if logged in (ocdb-cli user logout)
- __pwd__     Set the password for a user (see below)
- __update__  Update an existing user (see below)
- __whoami__  Get the current user (see below)

__General remarks on CLI syntax__

Command line arguments can be specified by single letters, e. g. -u for username or -p for password or
as words, such as --password or --username. For details see help for the respective command or subcommand,
e. g.:

ocdb-cli user --help

or

ocdb-cli user add --help

__Login User__:

The login procedure will ask for a user name and a password. You can specify the password 
as an option. However, under normal circumstances we advice to specify username only and  to 
use the command line prompt.

The example below will login a user with the user name 'scott'.
'scott' is a 'submitter' user. 'scott', after login, could
submit data to the system, but he does not have any
administrative privileges.

cli:
```bash
ocdb-cli user login --username scott --password tiger
```

python:
```python
api.login_user(username='scott', password='tiger')
```

cli:

```bash
ocdb-cli user logout
```

python:
```bash
api.logout_user()
```

__Who am I?__

To find out whether you are logged in or who is logged in, use:

cli:
```bash
ocdb-cli user whoami
```

python:
```python
api.whoami_user()
```

__Add User__ (admin only):

To add a user, specify the required user information. Arguments username, password, email and roles
are mandatory. _role_ could be either 'submit' (for any users) or 'admin' (for admin users only).

cli:
```bash
ocdb-cli user add -u <user_name> -p <password> -fn <user's first name> -ln <user's family name> -em <user's email> -ph <user's phone number> -r <role1> -r <role2>
```
In the command line the value for argument roles shall be written as admin, submit or ['submit','admin'], e.g.:
```bash
ocdb-cli user add --username super_user --password super_secret --roles ['submit','admin'] --email super_user@eum.int
```
Add further arguments as convenient.

python:
```python
api.add_user(username='<user_name>', password='<passwd>', email='<email>', roles=['<role1>, <role2>'])
```


__Get User Information__ (admin only):

Get details of a specific user, except password:

cli:
```bash
ocdb-cli user get scott
```

python:
```python
api.get_user(username='scott')
```

Users can request their own information without restrictions.


__Delete a User__ (admin only):

Delete a user by specifying the username.

cli (do not use key -u or --username!):
```bash
ocdb-cli user delete scott
```

python:
```python
api.delete_user(username='scott')
```

__Update an Existing User__ (admin or the respective user themselves only):

The following fields can be updated:

- first_name
- last_name
- email
- phone
- roles (admin only)

Even an admin user cannot change user id.

cli:
```bash
ocdb-cli user update --username scott --key <field to be updated> --value <your value>
```

python:
```python
api.update_user(<user_name>, key=<key>, value=<value>)
```

Users can update their own user details without restrictions. However, they have to specify their user name.


__Update own password__:

Any user can update his own password, after login.

cli:
```bash
ocdb-cli user pwd
```
You will be asked to input your current password and the new password.

Screenshot:

![](static/webui/cli_change_own_password.png)

python:
```bash
api.change_user_login(username=<username>,password=<password>,new_password=<new_password>)
```

*Forgotten password*

Please contact ServiceDesk@eumetsat.int [Subject: OCDB, forgotten password (username = …)]


__Update password of an existing user (admin only)__

Admins can reset a forgotten password for any user. To recover a user’s password,
use the pwd command as follows:

cli
```bash
ocdb-cli user pwd -u <username> -p <admin password> --new-password <new password>
```

python:

```bash
api.change_user_login(username='scott', password='tiger', new_password='lion')
```

Provide this <test_password> to the user and ask him/her to change
it immediately.


## Managing Submissions

__Upload a new submission__:
To contribute data through a new submission.

cli:
```bash
ocdb-cli sbm upload "<affiliation>/<experiment>/<cruise>" <data files list> -s <submission label> -ap -d <document files list>
```

&lt;data files list&gt; correspond to a list of comma separated full paths of measurement files.

&lt;document files list&gt; correspond to a list of comma separated full paths of document files.

-ap should be set **only** to allow data be available for the general public

python:
```python
api.upload_submission('<affilition>/<experiment>/<cruise>',dataset_files=('<file_path1>','<file_path2>',...),submission_id='<submission_label>', doc_files=('<file_path1>','<file_path2>',...),[allow_publication = <True/False>],[publication_date = '<yyyy/mm/dd>'])
```
*allow_publication* should be set to True **only** to allow data be available for the general public
*publication_date* should be set only when data can be available for the general public but only after the specified date


__Get Submission__ (admin only):
to get information for a specific submission

cli:
```bash
ocdb-cli sbm get IOPstudy2
```

python:
```python
api.get_submission('IOPstudy2')
```

Users can monitor their own submissions without restrictions.


__Get Submissions for a specific User__ (admin only):


cli:
```bash
ocdb-cli sbm user scott
```

python:
```python
api.get_submissions_for_user('scott')
```

Users can monitor their own submissions without restrictions.


__Delete Submission__ (admin only):


cli:
```bash
ocdb-cli sbm delete <submission-id>
```

python:
```python
api.delete_submission(<submission-id>)
```
Users can delete their own submissions without restrictions.


__Update Submission Status__ (admin only):

This command allows to manipulate the status assigned to any submission. Some status changes will have impact on
whether the data are searchable or not in the Database.

The following list shows the different stati and the impact on the accessibility when changing them:

- SUBMITTED: A dataset has been submitted. Usually also means that the data has issues. This will trigger
  the automated validation process
- VALIDATED: The data has been submitted and passed the quality checks (even in case any warning was raised)
- PROCESSED: The data has been processed into the database and is searchable, but only by admin users and the user who submetted it
- PUBLISHED: The data has been processed into the database and is publicly available
- CANCELED: The data submission has been canceled. Setting this status will remove the data from the database and will
  not be findable anymore. It can be still reprocessed again into the Database
- PAUSED: The user paused the submission. This indicates that the admin users shall not publish or process the data

cli:
```bash
ocdb-cli sbm status --submission-id <submission-id> --status <status>
```


python
```python
api.update_submission_status(<submission-id>, <status>)
```

Users can submit, cancel and pause their own submissions without restrictions.


__Download Submission File__:


This command will download a single submission file. Please be aware that the **version of the file is the one of the submission
status**. Do not use this feature to download data, instead use the "get_dataset" function of the API.

cli:
```bash
ocdb-cli sbmfile download -s <submission_label> --index <index> [--out-file <file_name>]
```

By default files are downloaded as 'download.zip'

python
```python
api.download_submission_file(<submission_label>,<index>, out_fn =  <file_name>)
```


__Upload Submission File__:


Both, measurement and documentation files, can be added to
**an existing submission**. Existing files will be replaced with updated files.


cli:
```bash
ocdb-cli sbmfile add --submission-id <submission_label> --file <local_file_path>  -t <type>
```

python
```python
api.add_submission_file(<submission_label>,<local_file>,<type>)
```
where _type_ could be 'MEASUREMENT' or 'DOCUMENT'


Both **existing measurement and documentation files** can be added to updated, replacing
them with a new file from local.

cli:
```bash
ocdb-cli sbmfile update --submission-id <submission_label> --file <local_file_path>  --index <index>
```

python
```python
api.update_submission_file(<submission_label>,<local_file>,<index>)
```

where *index* is the index of the file in the submission to be updated.


Users can update their own submission files without restrictions.


## General

__Get License__


```bash
ocdb-cli lic
```
