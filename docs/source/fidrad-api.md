# Managing FidRadDb

```markdown

!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!  A T T E N T I O N  !!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!

This part is still under development!
Changes can be made at any time. 

```
## The FidRadDB database

The FidRadDB is a database of characterisation and calibration files allowing the qualification of an
individual instrument and its measurements as FRM-certified. The main objective of the FidRadDB is to
gather in a same place all characterisation and calibration files of TRIOS and SEABIRD radiometers. To
be accepted in the FidRadDB, files need to be in accordance with the format provided by the Tartu University
laboratory (see also https://ocdb.readthedocs.io/en/latest/fidrad-database.html). Five types of files are
accepted in FidRadDB. Four of them are for radiometer characterisation and they contain angular responsivity
characterization results, polarization sensitivity characterization results, straylight characterization
results and thermal characterization results. One file is for the calibration. It should contain radiometric
calibration coefficients, linearity information, lamp and panel data. 

FidRadDB is also requested by the Hyper OCR community processor (HyperCP) to facilitate uncertainty budget
calculation. The [HyperCP](https://github.com/nasa/HyperCP/tree/master) can access all public cal/char files in
the open access mode as well as files submitted by the hyperCP user itself.  

The work steps around the FidRadDb consist of: 
- uploading the data
  - The cal/char files can be uploaded via WEB-GUI as well as via command line interface.
  - The files are automatically validated in this step
  - Should anything be wrong with the files, the user will be informed
- Obtain information about files already uploaded \
  This can be done by:
  - List the files available on the server
  - Search the history.log to find out more information regarding uploaded files
    - To find out when the file was uploaded?
    - Who uploaded the file?
    - Who downloaded the file?
    - How many downloads of a file have been made?
    - Has the file been deleted in the meantime and replaced by a revised version?
  - Get the last entries from the Hostory.log
    - Sometimes uploading and validating the files takes so long that the user receives 
      the error message "Gateway Timout Error" instead of a report.
      Don't worry!
      This does not mean that the upload failed or was aborted.
      It only means that the server is still processing the data, but has not managed 
      to do so within a certain time window.
      The processing of the data then continues in the background.
      When the server has processed the data, a user can check the history.log to see 
      whether everything worked or whether there were problems with individual files 
      and they were therefore not uploaded.
- Donwload a file
  - e.g. to use the file data for processing  
- Delete a file
  - e.g. if a file is to be replaced by a newer one, the existing file must be deleted first. 


There are three types of users that can work with FidRadDB, they will have different permissions:
- a guest user. No connection via login is needed. A guest user can only consult and download the open subset of the FidRadDB.
- a FidRadDB user. This user needs to be connected with its login and password. To register as a FidRadDB user please contact [EUMETSAT help desk](mailto:ops@eumetsat.int).
- an admin user. This status is restricted to FidRadDB managers only. 

The table below summarizes the FidRadDB commands permissions for the different users types. 

|        | Guest user | FidRadDB user | admin user |
| ------ | ------ | ------ | ------ |
|uploading | no | yes | yes |
|downloading| yes | yes | yes |
|deleting| no | yes but only its files | yes |
|list| yes | yes | yes |
|history.log| no | yes but only its files | yes |
|history.tail| no | yes but only its files | yes |
 
## Download the API

The API can be downloaded here: \
[https://github.com/eocdb/ocdb-client/tree/se_frm4soc_2_4](https://github.com/eocdb/ocdb-client/tree/se_frm4soc_2_4)

You have to switch to the branch "se_frm4soc_2_4".
As this API is currently still in the development phase, the new API is not available in the "master" branch. 

## Use the API in you python application 
If you want to integrate the new FidRadDB API in your own python application, you will find the functions in the file: 
[https://github.com/eocdb/ocdb-client/blob/se_frm4soc_2_4/ocdb/api/OCDBApi.py](https://github.com/eocdb/ocdb-client/blob/se_frm4soc_2_4/ocdb/api/OCDBApi.py):

```python

    def fidrad_upload(self, cal_char_files: Union[str, Sequence[str]],
                      doc_files: Optional[Union[str, Sequence[str]]]) -> JsonObj:
        ...
  
    def fidrad_history_tail(self, num_lines: int) -> JsonObj:
        ...
    
    def fidrad_history_search(self, search_string: str, max_num_lines: int) -> JsonObj:
        ...
    
    def fidrad_list_files(self, name_part: str) -> JsonObj:
        ...

    def fidrad_delete_file(self, file_name: str) -> JsonObj:
        ...
    
    def fidrad_download_file(self, file_name: str, output_dir: str) -> str:
        ...
```

[Here you can see how to instantiate the API before you can use it.](./ocdb-api-cli.html#python)

## Use the API via commandline

The following lines assume that Git and Miniconda are installed on your system.

First of all you have to check out the command line tool from github.
see [Download the API](#download-the-api)

Then please change to the directory "ocdb-client" that has just been checked out.

Now please create a new conda environment.

e.g.
```shell
# create an environment
conda create --clone base -n ocdb-client-test

# activite the environment
conda activate ocdb-clinet-test

# Your command line shall now be prefixed with (ocdb-clinet-test) 

# At last use this command, to install the command line app, configured for 
# development purposes. So the command line app can be used before the app 
# is deployed to conda.

# It is very important to not forget the dot at the end of the line.   
python -m pip install -e .
```

## First Use of the command line

Type in the command 'ocdb-cli -h' and you will see the following help page. 

```text
(ocdb-client-test) \path\to\the\github\repository\ocdb-client> ocdb-cli -h
Usage: ocdb-cli [OPTIONS] COMMAND [ARGS]...

  EUMETSAT Ocean Color In-Situ Database Client.

Options:
  --version       Show the version and exit.
  --server <url>  OCDB Server URL.
  -v, --verbose   OCDB client verbose reporting
  -h, --help      Show this message and exit.

Commands:
  conf      Configuration management.
  ds        Dataset management.
  fidraddb  FidRadDB management
  info      Get software infos.
  lic       Show license and exit.
  login     Login.
  logout    Log out current user if logged in.
  sbm       Submission management.
  sbmfile   Submission management.
  user      User management.
  version   Get the version of the client.
  whoami    Get current user.
```
In the list of available commands you will find the new 'fidraddb' command.

Type in 'ocdb-cli fidraddb -h'

```text
(ocdb-client-test) ...\ocdb-client> ocdb-cli fidraddb -h
Usage: ocdb-cli fidraddb [OPTIONS] COMMAND [ARGS]...

  FidRadDB management

Options:
  -h, --help  Show this message and exit.

Commands:
  delete          Will delete the file with the user defined name on the...
  download        Will download the file with the user defined name from...
  history-search  Returns a grep-like but bottom-up search result from...
  history-tail    Get history tail from FidRadDb <num_lines> (default 50...
  list            Lists the files available on the server.
  upload          Upload fidraddb cal/char files.
```
In order to get detailed help to this six new fidraddb commands, type in 'ocdb-cli fidraddb <the_command> -h'

In order to be able to really use this command line tool, the tool must be connected
to a server. By typing the command 'ocdb-cli conf' you can find out to 
which server the tool would currently send all requests.

If this is not the server address you expect, you can change the server
address by typing the command 'ocdb-cli conf server_url https://...'
```text
# e.g.
(ocdb-client-test) ...\ocdb-client> ocdb-cli conf server_url https://ocdb-stage.eumetsat.int

or in these development test phase 
(ocdb-client-test) ...\ocdb-client> ocdb-cli conf server_url https://www.brockmann-consult.de/frm4soc
```
And to check whether the new URL has been transferred correctly: 
```text
(ocdb-client-test) ...\ocdb-client> ocdb-cli conf
{
  "server_url": "https://www.brockmann-consult.de/frm4soc"
} 
```

## Uploading cal/char files to the server
Uploading can be done via command line tool or the python API.

For detailed information how to upload cal/char files please type in 'ocdb-cli fidraddb upload -h' or visit the class OCDBApi in the python file [OCDBApi.py](https://github.com/eocdb/ocdb-client/blob/se_frm4soc_2_4/ocdb/api/OCDBApi.py).
## List the files on the server
For detailed information how to upload cal/char files please type in 'ocdb-cli fidraddb list -h' or visit the class OCDBApi in the python file [OCDBApi.py](https://github.com/eocdb/ocdb-client/blob/se_frm4soc_2_4/ocdb/api/OCDBApi.py).
## Search information in the history.log file
For detailed information how to upload cal/char files please type in 'ocdb-cli fidraddb history-search -h' or visit the class OCDBApi in the python file [OCDBApi.py](https://github.com/eocdb/ocdb-client/blob/se_frm4soc_2_4/ocdb/api/OCDBApi.py).
## Get the end of the history.log file
For detailed information how to upload cal/char files please type in 'ocdb-cli fidraddb history-tail -h' or visit the class OCDBApi in the python file [OCDBApi.py](https://github.com/eocdb/ocdb-client/blob/se_frm4soc_2_4/ocdb/api/OCDBApi.py).
## Download a cal/char file from the server
For detailed information how to upload cal/char files please type in 'ocdb-cli fidraddb download -h' or visit the class OCDBApi in the python file [OCDBApi.py](https://github.com/eocdb/ocdb-client/blob/se_frm4soc_2_4/ocdb/api/OCDBApi.py).
## Delete a cal/char file from the server
For detailed information how to upload cal/char files please type in 'ocdb-cli fidraddb delete -h' or visit the class OCDBApi in the python file [OCDBApi.py](https://github.com/eocdb/ocdb-client/blob/se_frm4soc_2_4/ocdb/api/OCDBApi.py).

