# Fiducial radiometer database (FidRadDB)

The FidRadDB is a database of characterisation and calibrations files allowing the qualification of an individual instrument and its measurements as FRM-certified. The main objective of the FidRadDB is to gather in a same place all characterisation and calibration files of TRIOS and SEABIRD radiometers to easily estimate a full uncertainty budget with the community processor. FidRadDB allows different actions which are listed in https://ocdb.readthedocs.io/en/latest/fidrad-api.html. All the files recorded in FidRadDB are in accordance with the format provided by the University of Tartu laboratory whose specificities are listed bellow.  

## Calibration and characterisation files (cal/char files) in FidRadDB

**1. Identification of file type**

There are 5 different types of files that are accepted as a calibration or characterisation file.
The file type is recognized thanks to a keyword that should appear in the text file.
Five keywords are accepted (one for each file type). The keyword should be preceded
by “!” and should be alone on a line (see example). The five keywords are listed below.

**1.1 Calibration file**

```eval_rst
======= ==============================================================
Keyword Description
======= ==============================================================
RADCAL  radiometric calibration coefs & linearity, lamp and panel data
======= ==============================================================
```

**1.2 Chracterisation files**

```eval_rst
========= ==============================================================
Keyword   Description
========= ==============================================================
ANGDATA   angular responsivity characterization results
POLDATA   polarization sensitivity characterization results
STRAYDATA straylight characterization results
TEMPDATA  thermal characterization results
========= ==============================================================
```

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
2022-06-02 16:39:26

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
SAM_8268

# lab temperature (deg Celsius) during cal/char measurements
# type(s): single
[AMBIENT_TEMP]
21.0

# pixel no, wavelength (nm), semi-amplitude, uncertainty (k=2), angle of the max sensitivity plane (rad), uncertainty (rad, k=2)
# type(s): uint8, single, single, single, single, single
[CALDATA]
0	302.09	0.000E+00	0.000E+00	0.000E+00	0.000E+00
1	305.41	1.844E-02	3.111E-02	2.081E+02	2.741E+02
2	308.72	2.995E-02	2.607E-02	4.821E+01	8.037E+01
3	312.04	3.577E-03	3.247E-02	3.454E+01	1.189E+03
:
253	1139.19	1.342E-01	1.132E-01	3.853E+01	9.843E+01
254	1142.36	4.834E-02	3.305E-02	3.246E+02	8.711E+01
255	1145.53	2.149E-02	2.105E-02	7.005E+01	6.310E+01
[END_OF_CALDATA]
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
 

```eval_rst
================ ===================== =====================================================================
Metadata name    Ending code           Test
================ ===================== =====================================================================
[CALDATE]           x                  Valid date format: YYYY-MM-DD HH:MM:SS
[DEVICE]            x                  Device serial number. Either SAM_XXXX for TriOS or SATXXXX for
                                       Satlantic.
[CALDATA]        [END_OF_CALDATA]      File type = RADCAL. Table with 10 columns separated with tab. 
                                       File type = POLDATA. Table with 6 columns separated with tab representing pixel number, wavelength (nm), angle of the max sensitivity plane (rad), uncertainty (rad, k=2), semi-amplitude, uncertainty (rad, k=2) 
                                       File type = TEMPDATA. Table with 4 columns separated with tab representing pixel number, wavelength (nm), per-pixel thermal correction factor (deg-1) and uncertainty (deg-1, k=2).
[COSERROR]       [END_OF_COSERROR]     Table with 47 columns separated with tab.
[UNCERTAINTY]    [END_OF_UNCERTAINTY]  File type = ANGDATA. Table with 47 columns separated with tab.
[UNCERTAINTY]    [END_OF_UNCERTAINTY]  File type = STRAYDATA. Table with 256 columns separated with tab representing uncertainty associated to the straylight correction factors  
[LSF]            [END_OF_LSF]          Table with 256 columns separated with tab representing the straylight correction factors 
[AZIMUTH_ANGLE]     x                  Must be a float 
[PANEL_ID]          x                  Not empty character string
[LAMP_ID]           x                  Not empty character string
[USER]              x                  Not empty character string
[CALLAB]            x                  Not empty character string
[LAMP_CCT]          x                  Must be a float
[VERSION]           x                  Must be a float
[AMBIENT_TEMP]      x                  Must be a float
[REFERENCE_TEMP]    x                  Must be a float
[DEVICE_TEMP]       x                  Must be a float
[PANELDATA]      [END_OF_PANELDATA]    Table with 4 columns separated with tab representing the reflective plate wavelength (nm), bandwidth (nm), reflectance and uncertainty (%, k=2) 
[LAMPDATA]       [END_OF_LAMPDATA]     Table with 4 columns separated with tab representing the calibration lamp wavelength (nm), bandwidth (nm), irradiance (mW/m2/nm) and uncertainty (%, k=2)
================ ===================== =====================================================================
```

**3. Mandatory and optional metadata**

To be valid, a calibration file need to contain certain valid metadata whereas others are only optional. The table below summarize for each file type which metadata are mandatory and which are optional. If the all the mandatory metadata are present and valid the file is accepted in the FRM OCDB database.

```eval_rst
============== ======= ======= ====== ========= ========
Metadata       ANGDATA POLDATA RADCAL STRAYDATA TEMPDATA
============== ======= ======= ====== ========= ========
CALDATE           M       M       M      M         M
DEVICE            M       M       M      M         M
CALLAB            M       M       M      M         M
USER              O       O       O      O         O
VERSION           O       O       O      O         O
CALDATA           x       M       M      x         M
UNCERTAINTY       M       x       x      M         x 
COSERROR          M       x       x      x         x
LSF               x       x       x      M         x
PANEL_ID          x       x       O      x         x
LAMP_ID           x       x       O      x         x
AZIMUTH_ANGLE     M       x       x      x         x 
LAMP_CCT          x       x       O      x         x
AMBIENT_TEMP      x       O       O       O        O
REFERENCE_TEMP    x       x       x       x        M
DEVICE_TEMP       O       x       x       x        M
PANELDATA         x       O       x       x        x
LAMPDATA          x       O       x       x        x
============== ======= ======= ====== ========= ========
```

In this table "M" means that metadata is mandatory, "O" optional and "-" is used when the metadata is
not present for the file type.
