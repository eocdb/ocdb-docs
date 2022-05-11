# Validation configuration (admin only)

Every _in-situ_ measurement file sumbitted to the OCDB system is validated against a list of rules before being accepted by the system. 
The validation rules can be freely configured by admin users using the configuration file "validation_config.json"

The validation system checks both header fields and measurement records using the rules defined in the configuration file. Each rule relates to a section in the configuration file. 
Also, error and warning messages can be freely configured and associated to the rules.

The configuration file contains four major sections:

{  
"header": [],  
"record": [],  
"errors": [],  
"warnings": []  
}  
  
which are explained in details in the following sections.

## Header

This section in the configuration contains all checks to be executed on the measurement header entries. All checks need to belong to one of the following rule types.

### field_required
This set of rules checks if a required field is present in the header information and that the field is not empty.  A missing required header field always results in an error. Parameters are:


* **name**: denotes the name of the field. The name tag omits the forward slash and just contains the name
* **type**: always set to "field_required"
* **error**: the error message to be displayed, either direct or as a reference (see below).
Error messages can contain the tags
    * *{reference}*: resolves to the field name.  

Example:

    {
      "name": "investigators",
      "type": "field_required",
      "error": "@required_field_missing"
    }

### field_optional
This set of rules checks if an optional field is potentially present and if so that it is not empty. It issues a warning if the field is empty. Parameters are:

* **name**: denotes the name of the field. The name tag omits the forward slash and just contains the name
* **type**: always set to "field_optional"
* **warning**: the warning message to be displayed, either direct or as a reference (see below).
Warning messages can contain the tags
    * *{reference}*: resolves to the field name.
    
Example:

    {
      "name": "station",
      "type": "field_optional",
      "warning": "@field_value_missing"
    }  




### field_obsolete
This set of rules check if an obsolete header field is present in the header. If so, a warning message is issued. (This rule is included to deal with SeaBASS obsolete headers and for any future changes in OCDB.) 
Parameters are:

* **name**: denotes the name of the field. The name tag omits the forward slash and just contains the name
* **type**: always set to "field_obsolete"
* **warning**: the warning message to be displayed, either direct or as a reference (see below).
Warning messages can contain the tags
    * *{reference}*: resolves to the field name.

Example:

    {
      "name": "station_alt_id",
      "type": "field_obsolete",
      "warning": "@obsolete_field"
    }
    
    

### field_compare 
This set of rules checks that the values of header fields follow relational rules (e.g. stop day not before start day).
Parameters are:

* **reference_name**: denotes the name of the reference field. The name tag omits the forward slash and just contains the name
* **compare_name**: denotes the name of the comparand field. The name tag omits the forward slash and just contains the name
* **type**: always set to "field_compare"
* **operation**: one of the relational operators
    * \>=: greater than or equal
    * \>: greater than
    * !=: not equal
    * ==: equal
    * \<: lesser than 
    * \<=: lesser than or equal
* **data_type**: data type of the field value. Must be one of:
    * date: a date value formatted "YYYYmmdd"
    * number: a numerical value
    * string: a string value  
* **error**: the error message to be displayed, either direct or as a reference (see below).
Error messages can contain the tags
    * *{reference}*: resolves to the reference field name
    * *{ref_val}*: resolves to the value of the reference field
    * *{compare}*: resolves to the comparand field name
    * *{comp_val}*: resolves to the value of the comparand field
* **warning**: the warning message to be displayed, either direct or as a reference (see below).
Warning messages are overridden if error is present. Warning messages can contain the tags
    * *{reference}*: resolves to the reference field name
    * *{ref_val}*: resolves to the value of the reference field
    * *{compare}*: resolves to the comparand field name
    * *{comp_val}*: resolves to the value of the comparand field
    
Example:

    {
      "type": "field_compare",
      "reference": "start_date",
      "compare": "end_date",
      "operation": "<=",
      "data_type": "date",
      "error": "@header_start_after_finish"
    }


## Records

This set of rules performs checks on the record section covering two entities:

* field unit(s) 
* field value ranges 

The list of variable names to be validated is derived from the header field "fields" in the submitted file, defining the columns of the record section. 
The list of acceptable units for each variable are defined in the header section "units", as a comma separated list of unit names.


After these global checks have successfully been passed, all values are checked to be included in the defined value ranges for the variable. 
These checks are fill-value-aware, i.e. possible fill values as defined in the header section "missing" are treated as check-passed.
 
The check of the record content supports the following data types:

### Number record

This set of rules checks numerical measurement variable.  
Parameters are:

* **data_type**: always set to "number"
* **name**: the name of the variable
* **unit**: the list of physical units as comma separated values. Set to "none" or "unitless" if the variable is dimensionless.
* **lower_bound**: lower numerical bound for the variable values. Skip field if no lower bound is to be applied.
* **upper_bound**: upper numerical bound for the variable values. Skip field if no upper bound is to be applied.
* **unit_error**: the error message to be displayed in case of error related to the physical units, either direct or as a reference (see below).
Unit error messages can contain the tags
    * *{field_name}*: resolves to the variable name
    * *{unit}*: resolves to the required unit(s)
    * *{bad_unit}*: resolves to the unit detected as incorrect
* **value_error**: the error message to be displayed in case of error related to the variable values, either direct or as a reference (see below).
Value error messages can contain the tags
    * *{field_name}*: resolves to the variable name
    * *{line}*: resolves to the record line number where the error was detected
    * *{value}*: resolves to the erroneous value
    * *{lower_bound}*: resolves to the lower numerical bound (if defined)
    * *{upper_bound}*: resolves to the upper numerical bound (if defined)

Example:

    {
      "name": "adg",
      "unit": "1/m",
      "lower_bound": 0,
      "data_type": "number",
      "value_error": "@field_out_of_bounds",
      "unit_error": "@field_has_wrong_unit"
    } 
    
### Date record

This set of rules checks measurement variables containing a date value, formatted as "YYYYMMDD". Checks that the date format is correct, 
month and day values are within the standard boundaries, and that the date is after the min_date defined.
 
Parameters are:

* **data_type**: always "date"
* **name**: the name of the variable
* **min_year**: The lower bound of dates accepted as minimal year.

Example:

    {
      "name": "date_processed",
      "min_year": 1975,
      "data_type": "date"
    }

### Time record

This set of rules checks measurement variables defining a time, formatted as "hh:mm:ss". Checks that the time format is correct and the values for hours, minutes and seconds are within their ranges. 

Parameters are:

* **data_type**: always set to "time"
* **name**: the name of the variable
* **unit**: the list of physical units as comma separated values. Set to "none" or "unitless" if the variable is dimensionless.
* **unit_error**: the error message to be displayed in case of error related to the physical units, either direct or as a reference (see below).
Unit error messages can contain the tags
    * *{field_name}*: resolves to the variable name
    * *{unit}*: resolves to the required unit(s)
    * *{bad_unit}*: resolves to the unit detected as incorrect

Example:

    {
      "name": "time_processed",
      "unit": "hh:mm:ss",
      "data_type": "time",
      "unit_error": "@field_has_wrong_unit"
    }

### String record

This set of rules checks measurement variables containing a string. It checks that the string value is not empty.

Parameters are:

* **data_type**: always set to "string"
* **name**: the name of the variable
* **error**: the error message to be displayed, either direct or as a reference (see below).
Error messages can contain the tags
    * *{field_name}*: resolves to the variable name
    * *{line}*: resolves to the record line number where the error was detected

Example:

    {
      "name": "hplc_gsfc_id",
      "data_type": "string",
      "error": "@field_is_empty"
    }

## Errors and Warnings

The OCDB validation system allows to customize most of the error and warning messages. Messages can be either literal messages (i.e. these are displayed "as is" ) or can refer to a predefined message using the "@" character.

Example:

    {
      "name": "adg",
      "unit": "1/m",
      "lower_bound": 0,
      "data_type": "number",
      "value_error": "@field_out_of_bounds",
      "unit_error": "This field has a faulty unit"
    } 
    
The "value_error" is referring to a message template while the "unit_error" is using a literal error message.

The predefined messages are stored in the sections "errors" and "warnings" of the configuration file. A message is defined by a message name and the message text. Validation rules always refer to the name using the pattern "@name".

Example:

    "errors": [
        {
            "name": "south_north_mismatch",
            "message": "South_latitude is larger than north_latitude"
           }
    ]

The versatility of this message-system is supported by the possibility to use tags in the message templates. 
A tag is added to a message by writing the tag name in curly braces. Example:

    {
      "name": "field_has_wrong_unit",
      "message": "The units of '{field_name}', should be '{unit}', not '{bad_unit}'."
    } 

The possible tags for each validation rule is listed above in the descriptions of the rule parameters.


### Modifiers
A variable name can optionally be followed by any number of digits to e.g. denote the wavelength at which the measurement was taken. The name in the configuration file must be the raw name, 
without any suffix nor modifier; these are automatically stripped for the validation chores.
A list of acceptable suffix and modifiers are listed [here](ocdb-suffix-modifiers.md).
