# Search the OCDB using the GUI

All data the submitters have agreed to publish data searchable for the public.

The OCDB WebUI offers a graphical search interface. Main feature of this interface is the search text field.

## Free text search
Just entering any __whole word__ allows querying the Database for any file containing that specific __whole word__.

For example typing 'rrs412, sza412, chl_a' (without quotes), all the measurement files containing the word 'rrs412', 'sza412' or 'chl_a' in the file header are returned.
The free text search exhibits the following characteristics:

- whole words only: free text search does not allow search for substrings!
- it does not allow wildcards, such as '*' or '?'
- it is not case-sensitive
- words in the header are separated by '_' or any punctuation mark, e. g. comma or period

The following search terms will search for the respective parameters:
```
"a*ph"
"a*srfa"
"abs*"
```

Examples:

```
rrs412, sza412, chl_a    (searches for any of the three parameters)
Alexander                (searches for Alexander, e. g. being part of investigators)
Dubois                   (searches for Dubois, e. g. being part of investigators) 
Alexander_Dubois         (searches for Alxander_Dubois more precisely and this might result in a lower number of search results) 
```

__Please note:__
- Words starting with a digit, must be written in quotes
- Phrases must be written in quotes
- search terms using wildcards must be written without quotes

## Lucene Syntax

The search field allows using the so-called __Lucene syntax__ which enables you to search for strings and substrings as well as for ranges in specific metadata headers (see list below).

A concise description of the full Lucene query language syntax can be found [here](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html). 
Please note that the OCDB system does not support the complete syntax.

General syntax:

```
[metadata_header]: [search_term]
```

Example (Exact match):

```
investigators: Colleen
```

Returns all datasets where the field "investigators" exactly matches the term "Colleen". 

__Wild Card__:

Lucene syntax offers two wildcards; the "*" represents multiple characters, the "?" denotes a single character wildcard.

__Note:__ You cannot use a * or ? symbol as the first character of a search.

So the first example below returns all datasets with the investigators field containing  "Coll", surrounded by any number of characters,
whereas the second returns datasets with "Coll" followed by two undefined characters and 'n'.

```
investigators: Coll*
investigators: Coll??n
```

To search for any word containing the char 'a' use:
```
a*
```
To search for all parameters starting with 'a' use:
```
fields: ,a*
```
Keep in mind that the value for the metadata header fields is a comma-separated list of parameter names.


__Please note:__

- words starting with a digit, must be written in quotes
- words containing wildcards must be written without quotes
- the following special characters must be escaped by a preceding backslash
  if not written in quotes:
```
"+ - && || ! ( ) { } [ ] ^ " ~ * ? : \"
```
Examples:
```
\-999.0
missing: "-999.0" 
```

__Operators AND/OR__:

These operators allow to combine conditions. As expected, the "AND" implements a logical AND,
the "OR" represents the logical OR operation.

__Please note:__
- The operators AND and OR must be written in **upper** case.

```
investigators: Colleen* AND start_date: '2016-04-01'
investigators: Colleen* OR investigators: *Helge*
fields: ,chl_a*  or ,sza*
```

__Operator TO to search for ranges__:

Thus, searches with numeric ranges require that start and end values have the same length,
which is explicitly true for dates.

```
received: ["20191104" TO "20191108"]
start_date: ["19900101" TO "20211231"] AND end_date: ["20210101" TO "20221231"]
water_depth: ["10" TO "20"]
north_latitude: ["50" TO "60"]
```

The first example will list all files which:

- have been submitted between 2019.11.04 and 2019.11.08
- contain data in the period 2021.01.01 and 2021.12.31
- contain data measured in water_depths between 10 and 20 meters
- contain data in latitudes ranging between 50 and 60 degrees north

__Please note:__
- The operator TO must be written in **upper** case.
- All words are treated as strings, even if they represent numeric content.

When applying the operator 'TO', alphanumerical comparisons are used
(i. e. 'C' > 'B' is TRUE and '20' < '9' is TRUE as well!).

The following fields can be considered:

- __path__: Path where data files are stored
- __received__: Date when data were received (optional)
- __identifier_product_doi__: Product DOI (conditional, if available)
- __investigators__: Primary Investigators (PIs) of the experiment
- __affiliations__: Affiliations of the PIs (see path)
- __contact__: Contact (email address) of the PIs
- __experiment__: Identifier of the experiment (see path)
- __cruise__: Identifier of the cruise (see path)
- __station__: Name of the station where data were obtained (conditional, i. e. required if station does not appear in fields)
- __data_file_name__: Data file name
- __data_type__: Data type (e.g. scan, cast, above_water, ...) (mandatory)
- __data_status__: Could be preliminary, update or finally (optional but recommended)
- __start_date, end_date__: Start and end date
- __start_time, end_time__: Start and end time
- __north_latitude, south_latitude, west_longitude, east_longitude__:
  Bounding box coordinates
- __water_depth__: Water bottom depth at measurement point (in meters) (mandatory)
- __measurement_depth__: Measurement/Sample depth (in meters) (conditionally)
- __secchi_depth__: Secchi depth (in meters) (optionally but recommended)
- __missing__: Fill value for unvalid data (non-zero, common choice -9999)
- __below_detection_limit__: Numeric NULL value for values below detection limit (optional but recommended, common choice -8888)
- __above_detection_limit__: Numeric NULL value for values above detection limit (optional but recommended, common choice -7777)
- __delimiter__: Delimiter of data file e.g. 'tab', 'comma' or 'space'
  (e. g. 'delimiter: comma')

Examples:
```
path: "My_Affiliation/My_experiment/My_cruise"
station: "Blyth_NOAH"
start_date: "20160429"
start_time: "17:04:16 [GMT]"
north_latitude  "61.134032 [DEG]" 
missing: "-999.0" 
```

Consider that some of the metadata in the above list are not mandatory,
thus the search results for these metadata headers could be non-exhaustive.

## Search examples

### Products (Parameter)

1. Products can be chosen from a select list within the advanced search dialog.
   However, valid search results can only be obtained for products without postfix,
   e. g. wavelengths.
   
2. For postfixed products such as 'Rrs400' or 'SZA1020' the search text field
   shall be used. __All product names__ have to be followed by '*' or '?':
   
```
fields: SZA* OR fields: Chl_a*
```

### Product groups

The webbased search interface allows to restrict result sets to certain geophysical
variable types, organised by groups. They can be chosen from a selct list.
A list of groups and the variables covered is given in the table below.
Single product acronyms are fully described [OCDB standard field names and units](ocdb-standard-field-unit.md).

```eval_rst
============ ==========================================================================
Group        Description
============ ==========================================================================
a            Spectral absorption coefficients: a, ap, aph, ad, ag, ...
b            Spectral scattering coefficients: b, bp
bb           Spectral backscattering coefficients: bb, bbp, bbw, beta (VSF)
c            Spectral attenuation coefficients: c, cg, cp, cpg, cnw
kd           Distribution Coefficient: kd, kl, kpar, ku
AOP          Aerosol Optical Properties: ed, es, lt, lw, rrs, ...
AOT          Aerosol optical thickness: AOT, angstrom, water vapor (wvp), ozone (oz)
PAR          Photosynthetically Active Radiation: epar, eupar, par 
DC           Dissolved carbon: DIC, DOC, pCO2, total_Alkalinity, CDOM
PC           Particulated carbon: PC, PIC, POC
SPM          Suspended Particulate Matter: spm
nutrients    Si (sio4), N (n2_fix, nh4, no2, no2_no3, no3, tdn, urea),
             P (pn, po4, pon), oxygen
CTD          Hydrography: wt, sal/cond, sigmat
Chl          Chlorophyll, fluorometrically/spectrophotometrically derived:
             Chl*, phaeo, tpg
fluorescence Fluorescence (natf, stimf)
HPLC         HPLC derived phytoplankton pigments (allo, alpha*, anth, asta, beta-*, ...
productivity NPP, NCP, GPP, PP
============ ==========================================================================
```

For a detailed list of parameter names see: https://seabass.gsfc.nasa.gov/wiki/stdfields.

## Time range

In order to choose a time period covered by the data files, the metadata headers
start_date and end_date can be used as follows to search for data partly covering 1. Jan. to 31. Dec. 2021:

```
start_date: ["19000101" TO "20211231"] OR end_date: ["20210101" TO "20990101"]
```

### Region

1. You can use the interactive map to select a region by a rectangle or a polygon.
2. You can use the Python API or the OCDB command line interface to search for datasets by defining a certain region
   (see [OCDB Command Line Client and Python API](ocdb-api-cli.md)). 
