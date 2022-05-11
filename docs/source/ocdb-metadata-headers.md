# Metadata Headers

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

<!--
## Headers added by OCDB staff
The following fields (marked as obsolete in the validation rules) are added and managed by OCDB staff.
* **received** Date when the file has been submitted into the Database by investigators
* **processed** Date when the file has been processed and published into the Database
-->
