# Fiducial radiometer database (FidRadDB)

## Calibration and characterisation files (cal/char files)

**1. Identification of file type**

There are 5 different types of files that are accepted as a calibration or characterisation file.
The file type is recognized thanks to a keyword that should appear in the text file.
Five keywords are accepted (one for each file type). The keyword should be preceded
by “!” and should be alone on a line (see example). The five keywords are listed below.

**1.1 Calibration files**

| Keyword | Description |
| ------- | ----------- |
| RADCAL | radiometric calibration coefs & linearity, lamp and panel data |

**1.2 Caracterisation files**

| Keyword | Description |
| ------- | ----------- |
| ANGDATA | angular responsivity characterization results |
| POLDATA | polarization sensitivity characterization results |
| STRAYDATA | straylight characterization results |
| TEMPDATA | thermal characterization results |

In the following example file the keyword for file type recognition is on line 2 (!POLDATA):

```bash
!FRM4SOC_CP
!POLDATA
# polarization sensitivity characterization results

# comments start with # (ignored by the processor)
# no empty lines between the parameter signatures in [] and the parameter values
# parameters are case insensitive
# parameters can be inserted in any order, except the first two signatures
# columns are tab- or space-delimited

# file format version
# type(s): string(255)
[VERSION]
0.1

# calibration date
# type(s): fixed format as shown
[CALDATE]
yyyy-mm-dd hh:mm:ss

# calibration lab name
# type(s): string(255)
[CALLAB]
Tartu Observatory

# calibration lab person to contact
# type(s): string(255)
[USER]
Riho Vendt

# serial number of the instrument
# type(s): string(255)
[DEVICE]
SAM_8329

# polarization phase angle
# type(s): single
[POLANGLE]
0.07

# pixel no, angle of the max sensitivity plane (rad), uncertainty (rad, k=2), semi-amplitude, uncertainty (k=2)
# type(s): uint8, single, single, single, single
[CALDATA]
0	3.7514E-01	3.7514E-03	-8.3789E-03	1.6758E-04
1	3.9847E-01	3.9847E-03	-8.6576E-03	1.7315E-04
2	3.5573E-01	3.5573E-03	7.2163E-04	1.4433E-05
3	4.1062E-01	4.1062E-03	-2.1019E-03	4.2038E-05
:
```

Keywords are researched in any line of the file. If a certain keyword is not recognised or
occurs multiple times, the file is not accepted and the file submission process is stopped.

**2. Metadata**

Each file must contain a certain number of metadata elements. The metadata name is marked
by square brackets (e.g. [VERSION]). Information corresponding to the metadata is expected
on the line(s) below. For some metadata, information is contained into a single line whereas
others extend over multiple lines. In this last case, the last line is followed by the keyword
[END_OF_XXX], where XXX is the metadata name. Validity of metadata information is checked with
different tests depending on the metadata. Those tests are explained in the following table.

| Metadata name | Ending code | Test |
| ------ | ------ | ------ |
| [CALDATE] | - | Valid date format: YYYY-MM-DD HH:MM:SS|
| [DEVICE] | - | Device serial number. Either SAM_XXXX for TriOS or SATXXXX for Satlantic. |
| [CALDATA] | [END_OF_CALDATA] | File type = RADCAL. More than 5 lines, columns are separated by tabulations,  10 columns (i.e. elements per line) for TriOS senors and 8 for satlantic sensors. |
| | | File type = POLDATA. More than 5 lines, columns are separated by tabulations, 5 columns (i.e. elements per line) |
| | | File type = TEMPDATA. More than 5 lines, columns are separated by tabulations, 3 columns (i.e. elements per line) |
| [COSERROR] | [END_OF_COSERROR] | More than 5 lines, columns are separated by tabulations, 47 columns (i.e. elements per line) |
| [UNCERTAINTY] | [END_OF_UNCERTAINTY] | File type = ANGDATA. More than 5 lines, columns are separated by tabulations, 47 columns (i.e. elements per line)  |
| [UNCERTAINTY] | [END_OF_UNCERTAINTY] | File type = STRAYDATA. More than 5 lines, columns are separated by tabulations,  256 columns (i.e. elements per line)  |
| [LSF] | [END_OF_LSF] | More than 5 lines, columns are separated by tabulations, 256 columns (i.e. elements per line) |
| [AZIMUTH_ANGLE] | - | Must be a float | 
| [PANEL_ID] | - | Not empty character string |
| [LAMP_ID] | - | Not empty character string |
| [USER] | - | Not empty character string |
| [CALLAB] | - | Not empty character string |
| [LAMP_CCT] | - | Must be a float |
| [VERSION] | - | Must be a float |
| [AMBIENT_TEMP] | - | Must be a float |
| [REFERENCE_TEMP] | - | Must be a float |
| [DEVICE_TEMP] | - | Must be a float |
| [PANELDATA] | [END_OF_PANELDATA] | More than 5 lines, columns are separated by tabulations, 4 columns (i.e. elements per line) | 
| [LAMPDATA] | [END_OF_LAMPDATA] | More than 5 lines, columns are separated by tabulations,  4 columns (i.e. elements per line) |

**3. Mandatory and optional metadata**

To be valid, a calibration file need to contain certain valid metadata whereas others are only optional. The table below summarize for each file type which metadata are mandatory and which are optional. If the all the mandatory metadata are present and valid the file is accepted in the FRM OCDB database.

| | ANGDATA | POLDATA | RADCAL | STRAYDATA | TEMPDATA | 
| ------ | ------ | ------ | ------ | ------ | ------ |
| CALDATE | M | M | M | M | M |
| DEVICE | M | M | M | M | M |
| CALLAB | M | M | M | M | M |
| USER | O | O | O | O | O |
| VERSION | O | O | O | O | O |
| CALDATA | - | M | M | - | M |
| UNCERTAINTY | M | - | - | M | - |
| COSERROR | M | - | - | - | - |
| LSF | - | - | - | M | - |
| PANEL_ID | - | - | O | -| - |
| LAMP_ID | - | - | O | -| - |
| AZIMUTH_ANGLE | M | - | - | - | - |
| LAMP_CCT | - | - | O | -| - |
| AMBIENT_TEMP | - | O | O | O| O |
| REFERENCE_TEMP | - | - | - | - | M |
| PANELDATA | - | O | - | -| - |
| LAMPDATA | - | O | - | -| - |

In this table "M" means that metadata is mandatory, "O" optional and "-" is used when the metadata is
not present for the file type.
