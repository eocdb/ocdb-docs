# Metadata Headers

All SEABASS data files must start with a metadata header. The header starts with a line "/begin_header"
and ends with a line "/end_header". All metadata elements start with a slash, whereas comment lines start with a quotation mark.

For AERONET-OC data the following header could be used:

```bash
/begin_header
/investigators=Giuseppe_Zibordi
/affiliations=NA
/contact=giuseppe.zibordi@ec.europa.eu
/experiment=AErosol-RObotic-NETwork
/cruise=Abu_Al_Bukhoosh
/data_file_name=20020101_20220409_Abu_Al_Bukhoosh.csv
! Comments:
! AERONET metadata:
! Version = AERONET Version 3
! AERONET_Site_Name=Abu_Al_Bukhoosh
! Site_Elevation(m)=24.5
! Data_Quality_Level=lev20
! Last_Date_Processed=2021/01/27
! The following data are automatically cloud cleared and quality assured with pre-field and post-field calibration applied.
! Usage (in brief): Due to the research and development phase characterizing AERONET-Ocean Color, use of these data requires offering co-authorship to the Principal Investigator (PI).
! Calibration file: See https://aeronet.gsfc.nasa.gov/new_web/system_descriptions_calibration.html
/station=Abu_Al_Bukhoosh
/documents=Abu_Al_Bukhoosh.html
/calibration_files=system_descriptions_calibration.html
/data_type=above_water
/wavelength_option=multispectral
/start_date=20040927
/end_date=20080608
/start_time=08:52:35[GMT]
/end_time=03:59:17[GMT]
/north_latitude=25.495[DEG]
/south_latitude=25.495[DEG]
/east_longitude=53.14583[DEG]
/west_longitude=53.14583[DEG]
/water_depth=NA
/missing=-999.0
/delimiter=comma
/fields=date,time,sdy,lat,lon,altitude,SZA340,SZA380,SZA400,SZA412,SZA440,SZA443,SZA490,SZA500,SZA510,SZA531, ...
/units=yyyymmdd,hh:mm:ss,ddd,degrees,degrees,m,degrees,degrees,degrees,degrees,degrees,degrees,degrees,degrees,degrees,degrees, ...
/end_header
```

Below, the list of required and optional headers is shown, with description and examples.

Note that some optional headers are recommended: they are used to perform measurements quality check. Measurements for which these metadata are not provided, cannot be flagged as best quality.

## Required Headers

The following headers are required to be pass validation check

* __investigators__ Full name of the contributor(s) of the data file. Principal investigator is listed first. Format: Name_Surname.
<!-- A list of investigators already present in ocdb is available [here](ocdb-PI-affiliation-experiment-cruise.md/#investigators). -->

* __affiliations__ All investigator affiliations list. Format: Full_affiliation_name. Please do not exceed 25 characters.
<!-- A list of existing affiliations already in ocdb is available [here](ocdb-PI-affiliation-experiment-cruise.md/#affiliations). -->

* __contact__ An email address for one of the investigator(s) or a point of contact for the data file. 

* __experiment__ Full name long-term research project or funding program. It should be the same used in submission path. Please do not exceed 25 characters.
<!-- A list of existing experiments already in ocdb is available [here](ocdb-PI-affiliation-experiment-cruise.md/#experiments). -->

* __cruise__ The name of the specific cruise (or subset of the experiment) to which measurements are related to. Please do not exceed 25 characters. <!-- A list of existing cruises already in ocdb is available [here](ocdb-PI-affiliation-experiment-cruise.md/#cruises). -->

* __documents__ Comma separated list of documents provided during the submission process, related to the measurements included in the file.

* **data_type**
	Method used for the measurements. Accepted values include:
	- cast (for vertical profiles)
	- flow_thru (for continuous measurements as, e.g., underway flow through systems)
	- above_water (for above water surface radiometry measurements)
	- sunphoto (for sunphotometric measurements)
	- mooring (for moored and buoy measurements)
	- drifter (for drifter and drogue measurements)
	- scan (for discrete hyperspectral measurements)
	- lidar (for lidar/active remote-sensing measurements)
	- pigment (for any laboratory measured pigment data (e.g. fluorometry, spectrophotometry, HPLC))
	- bottle (for other types of measurements from water samples collected at discrete depths (e.g. nutrients))
	- diver (for measurements made by a diver)
	- auv (for measurements made by an Autonomous Underwater Vehicle)
	- airborne (for measurements made via aircraft)

* **calibration_files** Comma separated list of files containing coefficients and techniques used to calibrate the instruments used in data collection, also attached to submission.

* **water_depth** Water depth at the measuring point (in meters). If not known, set it to _NA_.

* __missing__ Value (only one!) used as a numeric placeholder for any missing data in the data file. This value should be a non-zero number, e.g. -9999. If your file includes below_detection_limit and above_detection_limit  values are also provided (obsolete), please set them to different values than missing.

* __delimiter__ Indicates how the columns of data are delimited. Accepted delimiters include tab, space, and comma. Only a single (1) delimiter per file.

* __fields__ Comma-separated list of the field names for each column of data included in the data file, one for each column. Empty columns are not admitted.

* __units__ Comma-separated of the units for each column of data included in the data file. Every value in /fields must have a corresponding value listed here.


## Optional Headers
The following headers are optional. Some of them, if not provided, are added by OCDB staff, after validation

* **start_date** The earliest date measurements in the file were collected (format: 'YYYYMMDD'). Added by OCDB staff after validation processing if not provided.
 
* **end_date** The latest date measurements in the file were collected (format: 'YYYYMMDD'). Added by OCDB staff after validation processing if not provided.

* **start_time** The earliest time measurements were collected on 'start_date' (format: 'HH:MM:SS [GMT]'), in Greenwich Mean Time (GMT). Added by OCDB staff after validation processing if not provided.

* **end_time** The latest time measurements were collected on 'end_date' (format: 'HH:MM:SS [GMT]'), in GMT. Added by OCDB staff after validation processing if not provided.

* **north_latitude** Maximum latidude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for latitudes south of the equator. Added by OCDB staff after validation processing if not provided.
 
* **south_latitude** Minimum latidude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for latitudes south of the equator. Added by OCDB staff after validation processing if not provided.

* **east_longitude** Maximum longitude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for longitude west of the Prime Meridian. Added by OCDB staff after validation processing if not provided.

* **west_longitude** Minimum longitude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for longitude west of the Prime Meridian. Added by OCDB staff after validation processing if not provided.

* **station** The name of the station where measurements in the file were collected.

* **data_file_name** The name of the data file submitted. <!-- Added by OCDB staff during submission processing if not provided. -->

* **data_status** The condition, or status, of the data file. The value _preliminary_ is used when the data are new and the investigator intends to analyze the data further. The value _update_ indicates the data are being resubmitted and informs users that an additional resubmission will occur in the future. The value final is used when the investigator has no intention of revisiting the data set. Recommended

* **identifier_product_doi** The DOI (Digital Object Identifier; see [http://www.doi.org/](http://www.doi.org/) associated with the experiment or the Dataset, if availabe

* **wavelength_option** Set to hyperspectral or multispectral. Required for products that have an associated wavelength.

* **instrument_model** Comma separated list of the model of the instruments whose measurements are being reported. Replace any spaces in the names with underscores. Recommended.

* **instrument_manufacturer** Comma seprataed list of the instrument manufacturers of the measurements that are being reported (e.g., Biospherical_Instruments_Inc.) Replace any spaces in the name with underscores. Recommended.

* **calibration_date** The most recent relevant calibration date for the primary instrument (format: 'YYYYMMDD'). Recommended.

* **cloud_percent** Percent cloud cover for the entire sky: 0 indicates no clouds and 100 indicates completely overcast. It could be also provided as a data field (field name: 'cloud'). Recommended.

* **secchi_depth** The secchi depth at the station where the data were collected (in meters). It could be also provided as a data field (field name: 'sz'). Recommended.

* **wave_height** The wave height at the station where the data were collected (in meters). It could be also provided as a data field (field name: 'waveht'). Recommended.   

* **wind_speed** The wind speed at the station where the data were collected (in meters per second). It could be also provided as a data field (field name: 'wind'). Recommended.

If the SEABASS file does not fulfill the validation requirements, a corresponding warning or error
is issued for each dataset. If a dataset contains one or more errors, the dataset will be mark es "Error" and
the whole submission it belongs to, will not be categorised as "Validated" but as "Submitted" only.

## Error messages

1. Metadata header does not start with "/begin_header": /begin_header tag missing
2. Metadata header does not end with "/end_header": /end_header tag missing
3. Header field "fields" is missing: SeaBASS header field "fields" required. See: https://seabass.gsfc.nasa.gov/wiki/metadataheaders#fields')
4. Header field "units" is missing: SeaBASS header field "units" required. See: https://seabass.gsfc.nasa.gov/wiki/metadataheaders#units')
5. Numbers of "fields" and "units" are unequal: Number of fields (X) does not match number of units (Y).
6. Numbers of "fields" and "columns" are unequal: Number of fields (X) does not match number of columns (Y).
7. Value is not numeric: Value must be numeric.
8. Neither the fields "start_date" and "end_date", nor the columns "date" and "time" exist:
   Acquisition time not properly encoded. For details see: https://seabass.gsfc.nasa.gov/wiki/stdfields "
                "or https://seabass.gsfc.nasa.gov/wiki/metadataheaders#Example%20Header.
9. Neither the fields "north_latitude", "south_latitude", "west_longitude" and "east_longitude" nor
   the columns "lat" and "lon" exist or the data format is wrong: Geolocation not properly encoded (for details
   see: https://seabass.gsfc.nasa.gov/wiki/metadataheaders#north_latitude).
10. A value between two column delimiters is missing: Value missing in data row X and column Y. Please use
	the placeholder as defined in metadata header “/missing”.
11. Header field "delimiter" is msissing: Missing delimiter tag in header
12. Delimiter valuedoes not correspond to "comma", "space" or "tab": Invalid delimiter-value in header
13. "Start_date" or "end_date" lack the suffix "[GMT]": No time zone given. Required all times be expressed as [GMT]
14. "Start_date" or "end_date" do not correspond to the syntax "yyyymmdd":
	Invalid date format. Format must correspond to YYYYMMDD.

Valid value ranges for year month day are (1900-current_year) (1-12) (1-31).

15. "Start_time" or "end_time" do not correspond to the syntax "hh:mm:ss":
	Invalid time format ... . Format must correspond to HH:MM:SS. See:
	https://seabass.gsfc.nasa.gov/wiki/metadataheaders#start_date

Valid value ranges for HH MM SS are (00-23) (00-59) (00-59).

16. A unit does not correspond to the unit pre-defined for the corresponding field:
    The units of '{field_name}', should be '{unit}', not '{bad_unit}'.

17. A value is less than the lower_bound value or greater than upper_bound:
    The field ... has value (...) outside expected range [{lower_bound} - {upper_bound}]

18. The data_type of any value is wrong: Invalid data type in field validation rule.

## Warning messages

1. A column name does not belong to the list of SEABASS fields:
   Variable not listed in valid variables.
   For details see: https://seabass.gsfc.nasa.gov/wiki/stdfields#Table%20of%20Field%20Names%20and%20Units
   