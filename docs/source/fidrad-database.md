## The FidRadDB database

The FidRadDB ("Fiducial Radiometer" Data Base) is a database containing information on radiometric
calibration and characterisations done on field Ocean Colour radiometers. 
The initial objective of the FidRadDB is to centralise all existing information on cal/char
of TriOS and SeaBird radiometers calibrated and characterised at the Tartu Observatory (University of Tartu, Estonia)
in the frame on the [FRM4SOC-2 project](https://frm4soc2.eumetsat.int/). Future endeavors may include cal/char coefficients obtained
in other contexts or for other instruments. To be accepted in the FidRadDB, cal/char files need to be in accordance with the format defined by the Tartu Obstervatory 
(for more information keep reading [below]([https://ocdb.readthedocs.io/en/latest/fidrad-database.html](https://ocdb.readthedocs.io/en/latest/fidrad-database.html#calibration-and-characterisation-files-cal-char-files-in-fidraddb))).
FidRadDB allows different actions (submitting new files, querying the database, downloading files, etc.) which are listed [here](https://ocdb.readthedocs.io/en/latest/fidrad-api.html).

FidRadDB is also accessible by the HyperInSPACE Community Processor ([HyperCP](https://github.com/nasa/HyperCP/tree/master)), 
which processes raw radiometric data and queries FidRadDB to extract the cal/char files (either instrument-specific of class-specific)
necessary to derive remote-sensing reflectance and normalized water-leaving radiance 
(among other OC products) including uncertainty budget calculation following metrologic standards.
HyperCP can ingest all public cal/char files available in FidRadDB in open access mode as well as files outside FidRadDB provided manually by the user. 

## Calibration and characterisation files (cal/char files) in FidRadDB

**1. Identification of file type**

Five types of files are allowed in FidRadDB:

- Radiometric calibration files (keyword=RADCAL). It should contain
    - lamp and panel irradiances,
    - radiometric calibration coefficients, and
    - dark and raw counts used to determine non-linearities in the radiometric response.

- The remaining four file types contain information on radiometric characterisation, in particular:
    - angular responsivity (keyword=ANGULAR)
    - polarization sensitivity (keyword=POLAR)
    - straylight (keyword=STRAY)
    - thermal response (keyword=THERMAL)

The file type is recognized thanks to the keyword (see above) that should appear in the second line of the text file. The keyword should be preceded
by “!” and should be alone on a line (see example).

**1.1 Calibration file**

```eval_rst
======= ==============================================================
Keyword Description
======= ==============================================================
RADCAL  radiometric calibration coefs & linearity, lamp and panel data
======= ==============================================================
```

RADCAL file example:

```bash
!FRM4SOC_CP
!RADCAL
# radiometric calibration coefs & linearity, lamp and panel data

# comments start with # (ignored by the processor)
# no empty lines between the parameter signatures in [] and the parameter values
# parameters are case insensitive
# parameters can be inserted in any order, except the first two signatures
# columns are tab- or space-delimited

[VERSION]
0.1

[CALDATE]
2022-06-27 09:48:49

[CALLAB]
Tartu Observatory

[USER]
Riho Vendt

[LAMP_ID]
TO_123

[PANEL_ID]
SG1234_2023

[DEVICE]
SAM_1234

# Correlated color temperature (K)
[LAMP_CCT]
2990.7

# wavelength (nm)     bandwidth (nm)  irradiane (mW/m2/nm) uncertainty (%, k=2)
[LAMPDATA]
300.00     0.00 1.5637     2.31
300.50     0.00 1.5923     2.29
301.00     0.00 1.6214     2.27
...
999.00     0.00 205.2464   3.51
999.50     0.00 205.2022   3.51
1000.00    0.00 205.1578   3.51
[END_OF_LAMPDATA]

# wavelength (nm)     bandwidth (nm)  reflectance      uncertainty (%, k=2)
[PANELDATA]
350.00     0.00 0.9890     1.20
360.00     0.00 0.9890     1.20
370.00     0.00 0.9890     1.20
...
1680.00    0.00 0.9480     0.50
1690.00    0.00 0.9460     0.50
1700.00    0.00 0.9520     0.50
[END_OF_PANELDATA]

[AMBIENT_TEMP]
21.0

# pixel no wavelength (nm) irradiane responsivity (unit depends on the device class)    uncertainty (%, k=2)   dark1 dark2 (content depends on the instrument class)     raw1 stdev1     raw2 stdev2
[CALDATA]
0     307.06     4     0.00 12    0.000000   64      0.00 32    0.00
1     310.37     0.000000   0.00 0.015465      0.020153   122.59     0.77 124.29     1.42
2     313.69     0.000000   0.00 0.015386      0.020376   164.19     0.75 163.29     1.27
3     317.01     0.000000   0.00 0.015388      0.020274   213.12     0.67 213.09     1.59
...
252  1139.36    0.000000   0.00 0.015429      0.019834   -1.85 0.66 -1.44 1.23
253  1142.52    0.000000   0.00 0.015495      0.019865   -2.61 0.65 -1.57 1.49
254  1145.68    0.000000   0.00 0.015523      0.019730   -2.65 0.65 -4.71 1.29
255  1148.83    0.000000   0.00 0.015997      0.020891   -2.95 0.68 -4.97 1.38
[END_OF_CALDATA]
```

**1.2 Characterisation files**

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
0     302.09     0.000E+00  0.000E+00  0.000E+00      0.000E+00
1     305.41     1.844E-02  3.111E-02  2.081E+02      2.741E+02
2     308.72     2.995E-02  2.607E-02  4.821E+01      8.037E+01
3     312.04     3.577E-03  3.247E-02  3.454E+01      1.189E+03
:
253  1139.19    1.342E-01  1.132E-01  3.853E+01      9.843E+01
254  1142.36    4.834E-02  3.305E-02  3.246E+02      8.711E+01
255  1145.53    2.149E-02  2.105E-02  7.005E+01      6.310E+01
[END_OF_CALDATA]
```

Keywords are detectable in any line of the file. If a certain keyword is not recognised or
occurs multiple times, the file is not accepted and the file submission process is stopped.

Find [here](https://github.com/nasa/HyperCP/tree/master/Data/Sample_Data/Instrument_Based_Characterizations/TriOS_Characterization_FICE22) examples of TriOS instrument-specific cal/char files in the FidRadDB format.

Find [here](https://github.com/nasa/HyperCP/tree/master/Data/Class_Based_Characterizations/TriOS_initial) examples of TriOS class-based cal/char files in the FidRadDB format.

Find [here](https://github.com/nasa/HyperCP/tree/master/Data/Sample_Data/Instrument_Based_Characterizations/SeaBird_Characterization_FICE22) examples of SeaBird instrument-specific cal/char files in the FidRadDB format.

Find [here](https://github.com/nasa/HyperCP/tree/master/Data/Class_Based_Characterizations/SeaBird_initial) examples of SeaBird class-based cal/char files in the FidRadDB format.

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
[CALDATA]        [END_OF_CALDATA]      File type = RADCAL. Table with 10 columns separated with tab representing pixel number, wavelength (nm), irradiance responsivity (units depending on instrument device class), uncertainty (%, k=2), dark value 1, dark value 2, raw counts dark 1, std. dev. dark 1, raw counts dark 2, std. dev. dark 2.
                                       File type = POLDATA. Table with 6 columns separated with tab representing pixel number, wavelength (nm), angle of the max sensitivity plane (rad), uncertainty (rad, k=2), semi-amplitude, uncertainty (rad, k=2) 
                                       File type = TEMPDATA. Table with 4 columns separated with tab representing pixel number, wavelength (nm), per-pixel thermal correction factor (deg-1) and uncertainty (deg-1, k=2).
[COSERROR]       [END_OF_COSERROR]     Table with 47 columns separated with tab.
[UNCERTAINTY]    [END_OF_UNCERTAINTY]  File type = ANGDATA. Table with 47 columns separated with tab representing pixel number, wavelength (nm), and each of the 45 sampled angles.
[UNCERTAINTY]    [END_OF_UNCERTAINTY]  File type = STRAYDATA. Table with 256 columns separated with tab representing uncertainty associated to the straylight correction factors.
[LSF]            [END_OF_LSF]          Table with 256 columns separated with tab representing the straylight correction factors.
[AZIMUTH_ANGLE]     x                  Must be a float.
[PANEL_ID]          x                  Not empty character string.
[LAMP_ID]           x                  Not empty character string.
[USER]              x                  Not empty character string.
[CALLAB]            x                  Not empty character string.
[LAMP_CCT]          x                  Must be a float.
[VERSION]           x                  Must be a float.
[AMBIENT_TEMP]      x                  Must be a float.
[REFERENCE_TEMP]    x                  Must be a float.
[DEVICE_TEMP]       x                  Must be a float.
[PANELDATA]      [END_OF_PANELDATA]    Table with 4 columns separated with tab representing the reflective plate wavelength (nm), bandwidth (nm), reflectance and uncertainty (%, k=2).
[LAMPDATA]       [END_OF_LAMPDATA]     Table with 4 columns separated with tab representing the calibration lamp wavelength (nm), bandwidth (nm), irradiance (mW/m2/nm) and uncertainty (%, k=2).
================ ===================== =====================================================================
```

**3. Mandatory and optional metadata**

To be valid, a calibration file needs to contain certain mandatory metadata, and may contain some specific optional metadata.
The table below summarizes for each file type which metadata are mandatory and which are optional. If all the mandatory metadata are present and valid the file is accepted in FidRadDB.

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
