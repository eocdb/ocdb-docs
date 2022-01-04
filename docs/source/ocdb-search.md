# Search the Database

All data the submittors have agreed to publish is searchable for the public. 
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

Lucene syntax offers two flavours of wildcards; the "*" represents multiple wildcard characters, the "?" denotes a 
single character wildcard. So the first example above returns all datasets with the investigators field containing 
"Colleen", surrounded by any number of characters, whereas the second returns datasets with "Colleen" preceded and followed by any single character.  


__Operators AND/OR__:

```
investigators: *Colleen* AND start_date: '2016-04-01'
investigators: *Colleen* OR investigators: *Helge*
```

These operators allow to combine conditions. As expected, the "AND" implements a logical AND, the "OR" represents the logical OR operation.

__Operators Lower/Greater Than__:

```
water_depth: > 10
water_depth: < 10
```

Allows to search for datasets where a field is greater that or smaller than a reference. For number fields the functionality is obvious. 
When applying the operator to String fields, alphanumerical comparisons are used (i.e. C>B is TRUE).

__Possible fields are__:

- __path__: path where data files are stored
- __received__: date data were received
- __identifier_product_doi__: Product DOI (if available)
- __investigators__: Primary Investigators (PIs) of the experiment
- __affiliations__: affiliations of the PIs.
- __contact__: ontact (email address) of the PIs.
- __experiment__: identifier of the experiment
- __cruise__: identifier of the cruise
- __data_file_name__: name of the original data file
- __data_type__: data type (e.g. scan, cast) (not mandatory)
- __documents__: Comma separated list of uploaded supplementary documents
- __data_status__: could be final, preliminary
- __water_depth__: Water depth at measurement point (in meters) (not mandatory)
- __measurement_depth__: Measurement depth (in meters) (not mandatory)
- __secchi_depth__: Secchi depth (in meters) (not mandatory)
- __missing__: Fill value for unvalid data
- __delimiter__: Delimiter of data file e.g. 'tab', 'comma'

Consider that some of the metadata in the above list are not mandatory (since they can be either in the file header as metadata or as data fields), thus the results of this kind of query for these fields could be not exaustive.

## Groups

The search interface allows to restrict result sets to certain geophysical variable types, organised by groups.
A list of groups and the variables covered is listed in the table below. Single products acronym are fully described [here](ocdb-standard-field-unit.md).

```eval_rst
============ =============================================================
Group        Description
============ =============================================================
a            Spectral absorption coefficients: a, ap, aph, ad, ag
b            Spectral scattering coefficients: b, bp
bb           Spectral backscattering coefficients: bb, bbp, beta (VSF)
c            Spectral attenuation coefficients: c, cg, cp, cpg
DC           Dissolved carbon: DIC, DOC, pCO2, alkalinity, CDOM
PC           Particulate carbon: PIC, POC
SPM          Suspended Particulate Matter
AOT          Aerosol optical properties: AOT, angstrom, water vapor, ozone
nutrients    Si, N, P, oxygen
CTD          Hydrography: Wt, Sal/Cond, sigmaT
fluorescence Fluorescence
productivity NPP, NCP, GPP, PP
Chl          Chlorophyll-a only (fluorometrically/spectrophotometrically derived)
HPLC         HPLC derived phytoplankton pigments
============ =============================================================
```


