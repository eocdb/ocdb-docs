# Contribute Data

The Database has been designed in order to guarantee easy access to data, a strong search engine, automation via command line access and interoperability with other Databases (in particular NASA SeaBASS Database).
For this reason, data can be contributed through the same simple data format, easily expandable and flexible, selected by NASA Ocean Biology Processing Group for the SeaBASS Database.

Users need to be registered to the Database in order to submit data.

Data submission can be done either via the [Database webUI ](ocdb-webui.md) or the [Command Line Interface as well as the Python API](ocdb-api-cli.md).

## Data Submission Policy
For data submission policy please refers to the [Applicable Data Policies](ocdb-data-policy.md) page.


## Data Format

In the data submission process, any file is automatically checked for its own format and completeness (validation configuration and the list of rules can be found respectively in [Validation configuration](ocdb-validation-config.md) chapter and in the JSON file validation_rules.json).

* Submitted data files need to be two-dimensional ASCII text files
* Data are preceded by metadata headers. The list of optional and requested metadata headers is available [here](ocdb-metadata-headers.md)
* Metadata headers section is introduced by 'begin_header' and closed by 'end_header' headers
* Any metadata header is preceded by '/'
* Comments can also be added inside the metadata headers section, but using a exclamation mark ('!') at the beginning of each comment line
* Headers should not include any white space. Words should be separated with an underscore. The only exception is for comment lines
* Columns may be delimited by spaces, tabs, or commas, as indicated in the 'delimiter' headers
* Field names and units are defined as a list using respectively 'fields' and 'units' headers. The complete list of standard field names and units is available [here](ocdb-standard-field-unit.md). Field names and units are not case sensitive.
* File names must not contain spaces or special characters (except for hyphens, underscores, and periods) and must be unique within a submission. Descriptive names including cruise and experiment names as well as date, depth or any other significant information is strongly recommended but not required.


## Example for metadata headers section
```bash
     /begin_header
     /investigators=Astrid_Bracher
     /identifier_product_doi=10.1594/PANGAEA.898929
     /affiliations=Alfred-Wegener-Institute_Helmholtz_Centre_for_Polar_and_Marine_Research
     /contact=Astrid.Bracher@awi.de
     /experiment=SO
     /cruise=SO234
     /data_file_name=Bracher_2019_SO234_db.txt
     /documents=see_comments
     /calibration_files=see_comments
     /data_type=cast
     /data_status=final
     /start_date=20140710
     /end_date=20140710
     /start_time=12:21:00 [GMT]
     /end_time=02:00:00 [GMT]
     /north_latitude=-20.1266 [DEG]
     /south_latitude=-29.695 [DEG]
     /east_longitude=58.82304 [DEG]
     /west_longitude=39.67942 [DEG]
     /water_depth=NA
     /wavelength_option=NA
     /instrument_model=NA
     /instrument_manufacturer=NA
     /calibration_date=NA
     /cloud_percent=NA
     /secchi_depth=NA
     /wave_height=NA
     /wind_speed=NA
     !
     ! COMMENTS
     !
     ! Citation:
     !  Bracher, Astrid; Cheah, Wee; Wiegmann, Sonja (2019): Phytoplankton pigment concentrations in the tropical Indian Ocean in July and August 2014 during RV Sonne cruises SO234 and SO235. Alfred Wegener Institute, Helmholtz Centre for Polar and Marine Research, Bremerhaven, PANGAEA, https://doi.org/10.1594/PANGAEA.898929. 
     !  Supplement to: Booge, Dennis; Schlundt, Michael; Bracher, Astrid; Endres, Sonja; Zäncker, Birthe; Marandino, Christa A (2018): Marine isoprene production and consumption in the mixed layer of the surface ocean - a field study over two oceanic regions. Biogeosciences, 15(2), 649-667, https://doi.org/10.5194/bg-15-649-2018
     !
     ! Data converted from PANGAEA.
     ! For docs and cal_files, see: https://doi.org/10.1594/PANGAEA.898929
     !
     /missing=-9999.
     /delimiter=comma
     /fields=station,sample,gear,date,time,lat,lon,depth,allo,asta,but-fuco,tot_chl_a,chl_b,chl_c3,chlide_a,diadino,diato,dino,dv_chl_a,dv_chl_b,fuco,hex-fuco,lut,neo,perid,phide_a,phytin_a,phytin_b,pyrophide_a,pyrophytin_a,viola,zea
     /units=none,none,none,yyyymmdd,hh:mm:ss,degrees,degrees,m,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3
     /end_header
```

## Documentation

For each submission, data files should be accompanied by documentation describing any measurement protocols adopted and Calibration/Instrument Reports and any other information useful to gather the quality of the data provided.
The reports should describe calibration equations and values, how the instruments were calibrated, and what types of corrections or data analysis were applied to derive the values submitted to the Database.
Users are also encouraged to submit any other information about deployments and/or cruises, they consider useful for data quality evaluation.

Documents can be submitted at the same time of data files via the [Database webUI ](ocdb-webui.md) or the [Command Line Interface as well as the Python API](ocdb-api-cli.md).

## Data Quality

Data submitted to the Database should be calibrated, depth-adjusted, unbinned, after quality checked analysis has been performed and bad quality measurements have been excluded. The process used to derive values provided and to perform the quality check analysis should be fully described in the documentation.
Any correction applied to data (e.g. normalization by surface irradiance, self-shading effect corrections etc.) should be listed and methods described.

On the other hand, a further check is done by Database administrators, after data has been submitted to the system, and before it is processed into the Database. 
This analysis allows to label each measurement or set of measurements with a good quality flag, adding a boolean variable to the data '[field_name]_qa' being 1 for data which pass the quality check, eventually used for Matchup Database files, 0 for all the other measurements.
The analysis is based on the completeness of protocol and quality check analysis description as well as some few further checks for:
- data status (should be the final version of data)
- clear sun and low cloudiness conditions and low Irradiance variability (for each cast) for radiometric measurements
- outliers removal

For this reason, users are strongly recommended to submit, together with  thedata, complete protocols and analysis descriptions, as well as any ancillary data they could provide.

Finally, information about uncertainty and/or replicates, should be reported (e.g. as standard deviation fields (named <name_field>_sd, e.g. "chl_sd"), together with bincount (e.g. <name_field>_bincount). 

Users submitting data could be of course involved in the quality check process by the administrator, whenever additional information or feedback are required.

