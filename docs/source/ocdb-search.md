# Search the Database

All data the submitters have agreed to publish data searchable for the public.

The OCDB WebUI offers a graphical search interface. Main feature of this interface is the search text field.
Just entering any __word__ allows also querying the Database for anyfile containing that specific word.

For example typing 'chl Rrs', all the mesurement files containing the word 'chl' or 'Rrs' in the header are returned.

This field also allows using the so-called __Lucene syntax__ which enables you to search for specific field values and also allows chaining. A concise description of the full Lucene query language syntax can be found [here](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html). 

Please note that the OCDB system does not support the complete syntax.

## Lucene Syntax

```
[field]: [expression]
```

__Exact Match__:

```
investigators: Colleen
```

Returns all datasets where the field "investigators" exactly matches the term "Colleen". 

__Wild Card__:

```
investigators: *Colleen*
investigators: ?Colleen?
```

Lucene syntax offers two flavours of wildcards; the "*" represents multiple wildcard characters, the "?" denotes a single character wildcard. So the first example above returns all datasets with the investigators field containing  "Colleen", surrounded by any number of characters, whereas the second returns datasets with "Colleen" preceded and followed by any single character.  


__Operators AND/OR__:

```
investigators: *Colleen* AND start_date: '2016-04-01'
investigators: *Colleen* OR investigators: *Helge*
```

These operators allow to combine conditions. As expected, the "AND" implements a logical AND, the "OR" represents the logical OR operation. Please note that the operators AND and OR must be written in **upper** case.

__Operators Lower/Greater Than__:

```
water_depth: >10
water_depth: <10
```

Please avoid spaces between operator and value!

__Operator TO to search for ranges__:

```
received: ["20191104" TO "20191108"]
start_date: ["19900101" TO "20211231"] AND end_date: ["20210101" TO "20221231"]
```
Please note that the operator TO must be written in **upper** case

Allows to search for datasets where a field is greater that or smaller than a reference. For number fields the functionality is obvious. 
When applying the operator to String fields, alphanumerical comparisons are used (i.e. C>B is TRUE).

__Possible fields are__:

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
- __original_file_name__: Name of the original data file (obsolete)
- __data_type__: Data type (e.g. scan, cast, above_water, ...) (mandatory)
- __documents__: Comma separated list of uploaded supplementary documents
- __data_status__: Could be preliminary, update or finally (optional but recommended)
- __water_depth__: Water bottom depth at measurement point (in meters) (mandatory)
- __measurement_depth__: Measurement/Sample depth (in meters) (conditionally)
- __secchi_depth__: Secchi depth (in meters) (optionally but recommended)
- __missing__: Fill value for unvalid data (non-zero, common choice -9999)
- __below_detection_limit__: Numeric NULL value for values below detection limit (optional but recommended, common choice -8888)
- __above_detection_limit__: Numeric NULL value for values above detection limit (optional but recommended, common choice -7777)
- __delimiter__: Delimiter of data file e.g. 'tab', 'comma' or 'space'

Examples:
```
path: My_Affiliation
```
Consider that some of the metadata in the above list are not mandatory (since they can be either in the file header as metadata or as data fields), thus the results of this kind of query for these fields could be not exaustive.

## Groups

The search interface allows to restrict result sets to certain geophysical variable types, organised by groups.
A list of groups and the variables covered is listed in the table below. Single products acronym are fully described [here](ocdb-standard-field-unit.md).

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