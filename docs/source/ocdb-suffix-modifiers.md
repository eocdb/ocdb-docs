# Field name modifiers and suffixes

## Modifiers
The table below lists acceptable modifiers to modify field names. They must be appended after the base name (and wavelength, if any) but before any suffix.

```eval_rst

.. csv-table:: Field modifiers
   :header: Field_modifier,Units,Description
   :widths: 30, 30, 100
   :stub-columns: 1
   :delim: ;

   _###ang; does not change base field's units; Collection angle. Append '_###ang' to the end of a field name to indicate the collection angle a measurment (such as VSF) was taken at, where '###' is replaced by the float or integer representation of an angle in degrees 
   _##cilo; does not change base field's units; Lower confidence interval, where ## is to be replaced with the percent the confidence interval was computed for
   _##ciup; does not change base field's units; Upper confidence interval, where ## is to be replaced with the percent the confidence interval was computed for 
   _ex###; does not change base field's units; Excitation wavelength. Append '_ex###' to the end of a field name to indicate the wavelength of excitation the measurement was taken at, where '###' is replaced by the float or integer represenation of wavelength in nm. May be used in combination with '_em###', as such: '<field>_ex###_em###', where '_ex###' preceeds '_em###' 
   _em###; does not change base field's units; Emission wavelength. Append '_em###' to the end of a field name to indicate the wavelength of emission the measurement was taken at, where '###' is replaced by the float or integer represenation of wavelength in nm. May be used in combination with '_ex###', as such: '<field>_ex###_em###', where '_ex###' preceeds '_em###' 
   _###filt; does not change base field's units; Filter size current observed measurements are larger than, where ### is the number of micrometers of the filter size Unless this suffix is used, it is assumed the methodology used a standard filter size. May be used in combination with '###prefilt', as such: '<field>_###filt_###prefilt)'
   _###prefilt; does not change base field's units; Filter size current observed measurements are smaller than, where ### is the number of micrometers of the filter size. Unless this suffix is used, measurements are assumed to be from unfiltered or whole water. May be used in combination with '###prefilt', as such: '<field>_###filt_###prefilt)'
   _###ppt; does not change base field's units; Parts per thousand, where ### indicates the solution's concentration that a measurement was taken in, as a floating point number or integer
   _###size; does not change base field's units; Median bin diameter in microns. Used as a suffix for the field 'PSD'
   _stokes1; does not change base field's units; First Stokes parameter for characterizing polarization
   _stokes2; does not change base field's units; Second Stokes parameter for characterizing polarization
   _stokes3; does not change base field's units; Third Stokes parameter for characterizing polarization
   _stokes4; does not change base field's units; Fourth Stokes parameter for characterizing polarization 
```

## Suffixes
The table below lists acceptable suffixes to modify field names. They must be appended at the end of field name, after any modifiers or wavelength. For any field including a suffix, a corresponding field (without suffix) must exist (e.g. if Rrs442.5_sd is provided, Rrs442.5 must exist).

```eval_rst

.. csv-table:: Field suffixes
   :header: Field_suffix,Units,Description
   :widths: 30, 30, 100
   :stub-columns: 1
   :delim: ;

   _abun; cell/L; Cell abundance for a particular (phytoplankton) taxonomic type
   _biovol; m^3/L; Bio-volume for a particular (phytoplankton) taxonomic type
   _carbon; ug/L; Carbon concentration for a particular (phytoplankton) taxonomic type
   _bincount; none; Number of records averaged into a bin or reported measurement specific to the prefix that _bincount is attached to. The field bincount can simply be used if the bincount applies to all forms of data in the file but this field suffix (i.e. '<field>_bincount') can be used multiple times in the same file for field-specific numbers
   _cv; unitless; Coefficient of Variation
   _sd; same as base field's units; Standard Deviation
   _se; same as base field's units; Standard Error
   _qa; none; added by OCDB staff, it is set to True when measurement pass internal quality checked and will be considered for matchups
```
