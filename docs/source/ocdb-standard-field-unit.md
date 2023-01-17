# Standard field names and units

Standard fields table below shows the list of valid field names and units to be used both when submitting measurements and querying the Database. 
In order to guarantee interoperability with NASA SeaBASS Database, [SeaBASS Standard Fields and Units](https://seabass.gsfc.nasa.gov/wiki/stdfields) have been reported here, together with OCDB dedicated variables. The table it is also constantly updated with new fields, whenever needed. 


```eval_rst

.. csv-table:: Standard fields
   :header: Field_Name,Units,Description
   :widths: 20, 10, 70
   :stub-columns: 1
   
13CO2_amps, amps, Peak intensity of 13CO2 measured using EIMS
3H_Leu, pmol/kg/hr, Net bacterial production rates (Gross Production - Respiration) are estimated by tracing the incorporation of 3H-labeled leucine into biomass and serve as a proxy for the flux of labile dissolved organic matter through bacteria.
3H_Leu_L, pmol/L/hr, Net bacterial production rates (Gross Production - Respiration) are estimated by tracing the incorporation of 3H-labeled leucine into biomass and serve as a proxy for the flux of labile dissolved organic matter through bacteria.
a, 1/m, Total absorption coefficient (aw + ap + ag)
a*ph, m^2/mg, Chlorophyll a specific absorption coefficient
a*srfa, m^2/mg, Specific absorption coefficient of Suwanee River Fulvic Acid standard
A578_A434, none, Ratio of absorbance of seawater using dyes 578 and 434
aa_alanine, nmol/L, alanine amino acid concentration
aa_arginine, nmol/L, arginine amino acid concentration
aa_aspartic_acid, nmol/L, aspartic acid amino acid concentration
aa_beta-alanine, nmol/L, beta-alanine amino acid concentration
aa_gamma_amino_butyric_acid, nmol/L, gamma_amino_butyric_acid amino acid concentration
aa_glutamic_acid, nmol/L, glutamic_acid amino acid concentration
aa_glycine, nmol/L, glycine amino acid concentration
aa_histidine, nmol/L, histidine amino acid concentration
aa_isoleucine, nmol/L, isoleucine amino acid concentration
aa_leucine, nmol/L, leucine amino acid concentration
aa_lysine, nmol/L, lysine amino acid concentration
aa_methionine, nmol/L, methionine amino acid concentration
aa_phenylalanine, nmol/L, phenylalanine amino acid concentration
aa_serine, nmol/L, serine amino acid concentration
aa_taurine, nmol/L, taurine amino acid concentration
aa_threonine, nmol/L, threonine amino acid concentration
aa_tyrosine, nmol/L, tyrosine amino acid concentration
aa_valine, nmol/L, valine amino acid concentration
aaer, 1/m, Absorption coefficient of atmospheric aerosols
abs, unitless, Absorbance
abs*, m^2/mg, Carbon specific absorbance
abs_ad, unitless, Absorbance (Optical Density) of non-algal detritus
abs_ag, unitless, Absorbance (Optical Density) of Gelbstoff
abs_ap, unitless, Absorbance (Optical Density) of particles (ad + aph)
abs_blank_ad, unitless, Absorbance of a blank (or unused) filter pad for non-algal detritus.
abs_blank_ag, unitless, Absorbance of a blank (or unused) filter pad for Gelbstoff.
abs_blank_ap, unitless, Absorbance of a blank (or unused) filter pad for particles.
abs_nacl, unitless, Absorbance of NaCl solution (use with the _###ppt suffix)
abs_zero, unitless, Absorbance of a blank (or unused) filter pad; collected after the baseline but before the formal "blank" scans. Data should be spectrally flat about zero.
abun, cells/L, Concentration of cells observed
abun_bacterioplankton, cells/L, Abundance concentration of bacterioplankton
abun_phyto, cells/L  , Abundance concentration of phytoplankton
abun_zoop, organisms/L, Abundance concentration of zooplankton
abundance, none, Number of cells observed
ad, 1/m, Absorption coefficient of non-algal detritus or particles (NAP)
ad_model, 1/m, Absorption coefficient of non-algal detritus or particles (NAP) that has been exponentially fit or smoothed
ad_unc, 1/m, Accumulated estimate of standard uncertainty associated with the derivation of the absorption coefficient of non-algal detritus (ad) via error propagation through the absorption equation. See section 5.3.4 of IOCCG's "Volume 1: Inherent Optical Property Measurements and Protocols: Absorption Coefficient" (2018).
adg, 1/m, Absorption coefficient of non-algal detritus + Gelbstoff (ad + ag)
ag, 1/m, Absorption coefficient of Gelbstoff
ag_model, 1/m, Absorption coefficient of gelbstoff (i.e.; CDOM) that has been exponentially fitted or smoothed
agp, 1/m, Absorption coefficient of Gelbstoff + particles (ag + ap)
Allo, mg/m^3, HPLC Alloxanthin
alpha-beta-Car, mg/m^3, HPLC Alpha (Beta;epsilon) + Beta (Beta;beta) Carotenes
altitude, m, Altitude above sea level
AMC, umol, Concentration of 7-Amino-4-methylcoumarin's fluorescent molecules without an associated substrate (used for the calibration curve in flow cytometry).
AMC-Leu, umol/L/hr, Rate of substrate cleavage for L-Leucine-7-amido-4-methylcoumarin hydrochloride
amplitude,  unitless,  Amplitude use during calibration of oxygen sensors
angstrom, unitless, Angstrom exponent
Anth, mg/m^3, HPLC Antheraxanthin
AOT, unitless, Aerosol Optical Thickness (sometimes referred to as tau or taua)
AOU, umol/kg, Apparent Oxygen Utilization
AOU_kg, mL/L, Apparent Oxygen Utilization
ap, 1/m, Absorption coefficient of particles (ad + aph)
ap_unc, 1/m, Accumulated estimate of standard uncertainty associated with the derivation of the absorption coefficient of particles (ap) via error propagation through the absorption equation. See section 5.3.4 of IOCCG's "Volume 1: Inherent Optical Property Measurements and Protocols: Absorption Coefficient" (2018).
aph, 1/m, Absorption coefficient of phytoplankton
aph_model, 1/m, Absorption coefficient of phytoplankton that has been exponentially fit or smoothed
aph_unc, 1/m, Accumulated estimate of standard uncertainty associated with the derivation of the absorption coefficient of phytoplankton (aph) via error propagation through the absorption equation. See section 5.3.4 of IOCCG's " Volume 1: Inherent Optical Property Measurements and Protocols: Absorption Coefficient" (2018).
Ar_amps, amps, Peak intensity of Argon (Ar) measured using EIMS
area_based_diameter, um, Area-based diameter of the target detected within the ROI determined by means specified in the image processing method or protocol document.
area_cross_section, um^2, Cross-sectional area of the target detected within the ROI determined by means specified in the image processing method or protocol document.
asrfa, 1/m, Absorption coefficient of Suwanee River Fulvic Acid standard
associated_file_types, none, File type of an associated file. Please contact SeaBASS staff before using this field to verify that your file type is supported. Valid entries for this field are: DNA-FASTQ; DNA-FASTA (for files relating to DNA analysis); BENTHIC (for images relating to benthic type and cover); metadata_sediment_trap (for additional trap informations such as coordinates or ancillary data); imaging_UVP (for UVP imagery and ancillary data);imaging_flowcam (for Flow Cam imagery and ancillary data); imaging_epifluorescence (for imagery collected with epifluorescence microscopy); and imaging_microscopy (for any images collected using traditional microscopy). If multiple entries are applicable; separate them with the pipe character: | To be used with field: associated_files
associated_files, none, File name of an associated file. Must be used with associated_file_type. Please include the file suffix in the entry. If multiple entries are applicable; separate them with the pipe character: | To be used with field: associated_file_type If individual files are referenced but are part of a TAR archive bundle; be sure to use the associated_archives and associated_archive_types headers.
associatedMedia, none, A unique persistent identifier of the media associated with the occurrence. The field provides the unique imagery file name corresponding to the source of the ROI or a URL pointing to a permanent landing page for the ROI image.
Asta, mg/m^3, HPLC Astaxanthin
At, degreesC, Air temperature
aw, 1/m, Absorption coefficient of water
b, 1/m, Total scattering coefficient (bw + bp)
Ba_138_134_d_delta, per_mil, Total Ba-isotopic composition
bactP, pmol/L/hr   , Bacterioplankton production
bb, 1/m, Total backscattering coefficient (bbw + bbp)
bb_counts, counts, Uncalibrated total backscattering coefficient (bbw + bbp)
bbp, 1/m, Backscattering coefficient of particles
bbp_bp, unitless, Ratio of the backscattering coefficient of particles (bbp) to the total backscattering coefficient (bp)
bbp_gamma, unitless, Backscattering coefficient of particles spectral slope (the exponent of the power-law fit)
bbw, 1/m, Backscattering coefficient of water
BChl_a, mg/m^3, HPLC Bacteriochlorophyll a
benthic_type, none, Description of the benthic seafloor community or substrate.
beta-beta-Car, mg/m^3, HPLC Beta-Carotene (Beta;beta-Carotene)
beta-epi-Car, mg/m^3, HPLC Alpha-Carotene (Beta;epsilon-Carotene)
beta-psi-Car, mg/m^3, HPLC Gamma-Carotene (Beta;psi-Carotene)
bin_depth, m, Nominal or center depth for each data bin
bin_diameter_center, m, size bin limit for particle size distribution measurements (e.g. for coulter counter)
bin_diameter_lower, m, size bin limit for particle size distribution measurements (e.g. for coulter counter)
bin_diameter_upper, m, size bin limit for particle size distribution measurements (e.g. for coulter counter)
bincount, none, Number of records averaged into a bin or reported measurement
biomass_microzoop, mg/m^3, Microzooplankton biomass
biotic_class, none, Biotic Class; Biotic Component; level 2 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
biotic_community, none, Biotic Community; Biotic Component; level 5 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
biotic_group, none, Biotic Group; Biotic Component; level 4 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
biotic_setting, none, Biotic Setting; Biotic Component; level 1 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
biotic_subclass, none, Biotic Subclass; Biotic Component; level 3 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
biovol_bacterioplankton, um^3/cell, Mean (estimated) volume per bacterial cell.
biovolume, um^3, Biovolume for the target detected within the ROI determined by means specified in the biovolume calculation method or protocol document.
bottle, none, Number used to identify a specific bottle within an array of bottle samples collected
bp, 1/m, Scattering coefficient of particles
BSi, mmol/m^3, Biogenic silica
But-fuco, mg/m^3, HPLC 19'-Butanoyloxyfucoxanthin
bw, 1/m, Scattering coefficient of water
c, 1/m, Beam attenuation coefficient
C2H3N_H, ppbv, VOCC concentration of (C2H3N)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
C2H4O_H, ppbv, VOCC concentration of (C2H4O)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
C2H6S_H, ppbv, VOCC concentration of (C2H6S)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
C3H6O_H, ppbv, VOCC concentration of (C3H6O)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
C5H8_H, ppbv, VOCC concentration of (C5H8)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
C6H6_H, ppbv, VOCC concentration of (C6H6)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
Cantha, mg/m^3, HPLC Canthaxanthin
cast, none, Cast id or number
cdmf, volts, CDOM fluorescence (may be used in combination with suffixes _ex### and/or _em###; like so: cdmf_ex###_em###; ex = excitation wavelength; em = emission wavelength)
cdmf_counts, counts, CDOM fluorescence (see "cdmf") expressed in units of counts
cdom, mg/m^3, Concentration of chromophoric dissolved organic matter
cdomf, ppb, calibrated CDOM fluorescence measurements expressed in ppb QSE (CDOM fluorescence may be used in combination with suffixes _ex### and/or _em###; like so: cdomf_ex###_em###; ex = excitation wavelength; em = emission wavelength)
cg, 1/m, Attenuation coefficient of Gelbstoff
cgp, 1/m, Attenuation coefficient of Gelbstoff + particles (c - cw = agp + bp)
CH4O_H, ppbv, VOCC concentration of (CH4O)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
CH4S_H, ppbv, VOCC concentrations of (CH4S)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
Chl, mg/m^3, Chlorophyll a derived fluorometrically/spectrophotometrically (e.g.; "extracted" Chl)
Chl_a, mg/m^3, HPLC Chlorophyll a (MV_Chl_a plus allomers and epimers)
Chl_a_allom, mg/m^3, HPLC Chlorophyll a allomers
Chl_a_prime, mg/m^3, HPLC Chlorophyll a epimer
Chl_b, mg/m^3, HPLC Chlorophyll b
Chl_c, mg/m^3, HPLC Chlorophyll c
Chl_c1, mg/m^3, HPLC Chlorophyll c1
Chl_c1c2, mg/m^3, HPLC Chlorophyll c1 + c2 + Mg_DVP
Chl_c2, mg/m^3, HPLC Chlorophyll c2
Chl_c3, mg/m^3, HPLC Chlorophyll c3
Chl_experiment, mg/m^3, Chlorophyll a derived via experiment; or experimental methods. See specific documentation for more information.
Chl_lineheight, mg/m^3, Chlorophyll a derived using particulate absorption line height method
Chl_stimf, mg/m^3  , Chlorophyll a derived from a calibrated in situ fluorometer
Chlide_a, mg/m^3, HPLC Chlorophyllide a
Chlide_b, mg/m^3, HPLC Chlorophyllide b
chors_id, none, CHORS HPLC processing identification number
cloud, %, Percent cloud cover
cnw, 1/m, Attenuation coefficient of Gelbstoff + particles (obsolete; see cgp)
CO2_amps, amps, Peak intensity of CO2 measured using EIMS
conc_Ba_total, nmol/L, Total concentration of Barium
conc_particles, particles/L, Concentration in particles per liter
conc_Pb_210, dpm/L, Concentration of Lead 210
conc_Po_210, dpm/L, Concentration of Polonium 210
conc_Th_234, dpm/L, Concentration of Thorium 234
conc_U_238, dpm/L, Concentration of Uranium 238
cond, mmho/cm, Conductivity
cp, 1/m, Beam attenuation coefficient of particles (ap + bp)
cp_gamma, unitless, Particulate beam attenuation spectral slope (the exponent of the power-law fit)
cp_gamma_RMSE, unitless, Root mean squared error (RMSE) evaluation of the goodness of fit of cp_gamma (spectral slope)
Croco, mg/m^3, HPLC Crocoxanthin
cw, 1/m, Beam attenuation coefficient of water (aw + bw)
cycle, none, Incrementing counter describing the sampling interval of the instrument. Relevant to the PTR-TOF/MS.
data_provider_category_automated, none, A category used by the data provider to name the organism or particle for an automated classification; not necessarily a scientific name (e.g.; pennate or detritus).
data_provider_category_manual, none, A category used by the data provider to name the organism or particle for a manual identification; not necessarily a scientific name.
date, yyyymmdd, Sample date
date_end, yyyymmdd, Date sampling stopped (only needed for extended measurements; e.g.; multi-day integration measurements for sediment traps; also see "time_end")
date_processed, yyyymmdd, Date the sample was processed
date_recovery, yyyymmdd, Date instrumentation was recovered from the field (only needed for extended measurements; e.g.; multi-day integration measurements for sediment traps; also see "time_recovery")
date_resurface, yyyymmdd, Date instrumentation resurfaced from a submerged deployment (e.g.; used for non-buoyant sediment traps)
date_start, yyyymmdd, Date sampling began (only needed for extended measurements; e.g.; multi-day integration measurements for sediment traps; also see "time_start")
day, dd, Sample day
DCAA, nM, Dissolved combined amino acid concentration
depth, m, Depth of measurement
dewpoint, degreesC, Dew point temperature
Diadchr, mg/m^3, HPLC Diadinochrome
Diadino, mg/m^3, HPLC Diadinoxanthin
Diato, mg/m^3, HPLC Diatoxanthin
DIC, umol/kg, Dissolved inorganic carbon (per kg)
DIC_L, umol/L, Dissolved inorganic carbon (per L; preferred units for satellite val)
Dino, mg/m^3, HPLC Dinoxanthin
DMSA, ppt, Concentration of dimethyl sulfide (DMS) in the atmosphere
DMSSW, nmol/L, Concentration of dimethyl sulfide (DMS) in sea water
DNA, mg/m^3, DNA (DeoxyriboNucleic Acid) concentration within a water volume
DOC, umol/kg, Dissolved organic carbon (per kg)
DOC_L, umol/L, Dissolved organic carbon (per L; preferred units for validation)
DP, mg/m^3, Total diagnostic pigments (PSC + Allo + Zea + Tot_Chl_b)
DV_Chl_a, mg/m^3, HPLC Divinyl Chorophyll a
DV_Chl_b, mg/m^3, HPLC Divinyl Chorophyll b
E_scalar, uW/cm^2/nm, Scalar irradiance
Echin, mg/m^3, HPLC Echinenone
Ed, uW/cm^2/nm, Downwelling irradiance (planar measurements only; for scalar measurements use scalar fields)
Ed_scalar, uW/cm^2/nm, Downwelling scalar irradiance
EdGND, volts, Dark current values for Ed sensor
EdPAR_scalar, uE/cm^2/s, Downwelling scalar PAR irradiance
elapsed_time, seconds, Elapsed time
Elw, uW/cm^2, Downwelling irradiance over the infrared spectrum; 3 to 40 um
Epar, uE/cm^2/s, Profiled PAR (planar measurements only; for scalar measurements use scalar fields)
EPAR_scalar, uE/cm^2/s, Scalar PAR irradiance
epi-epi-Car, mg/m^3, HPLC Epsilon-Carotene (Epsilon;epsilon-Carotene)
equivalent_spherical_diameter, um, Equivalent spherical diameter of the target detected within the ROI determined by means specified in the image processing method or protocol document.
Es, uW/cm^2/nm, Downwelling surface irradiance (planar measurements only; for scalar measurements use scalar fields)
EsGND, volts, Dark current values for Es sensor
Esky, uW/cm^2/nm, Downwelling sky irradiance
Esun, uW/cm^2/nm, Downwelling sun irradiance (direct normal solar irradiance)
Esw, uW/cm^2, Downwelling irradiance over the solar spectrum; 0.3 to 3 um
Et-8-carot, mg/m^3, HPLC Ethyl-apo-8'-carotene
Et-chlide_a, mg/m^3, HPLC Ethyl Chlorophyllide a
Et-chlide_b, mg/m^3, HPLC Ethyl Chlorophyllide b
Eu, uW/cm^2/nm, Upwelling irradiance
Eu_scalar, uW/cm^2/nm, Upwelling scalar irradiance
EuGND, volts, Dark current values for Eu sensor
EuPAR, uE/cm^2/s, Profiled upwelling PAR (planar measurements only; for scalar measurements use scalar fields)
EuPAR_scalar, uE/cm^2/s, Upwelling scalar PAR irradiance
F-initial, unitless, Minimum fluorescence in darkness. Fast Repetition Rate Fluorescence measurement; commonly abbreviated as F0
F0, uW/cm^2/nm, Extraterrestrial solar irradiance
fecalpellet_production_carbon_carbonweight, mg/mg/hr, Zooplankton fecal pellet production in Carbon (carbon weight)
fecalpellet_production_carbon_dryweight, mg/mg/hr, Zooplankton fecal pellet production in Carbon (dry weight)
FL-A, arbunits, Area of the signal of emission by fluorescence (flow cytometry). May be used with _ex###_em### field modifiers.
FL-H, arbunits, Height of the signal of emission by fluorescence (flow cytometry). May be used with _ex###_em### field modifiers.
flux_ATN, m^2_m^-2_d^-1, Rate of increase of accumulated particles' attenuance (characterize methods with flux_sampling_method; etc.)
flux_Ba, mmol_m^-2_d^-1, Flux of barium (characterize methods with flux_sampling_method; etc.)
flux_bSi, mmol_m^-2_d^-1, Flux of biogenic silica (characterize methods with flux_sampling_method; etc.)
flux_calibration_method, none, Flux_calibration_method must be included to characterize flux measurements in a SeaBASS file (if relevant; otherwise set to missing value); along with flux_sampling_method; flux_submethod; and flux_sinking_speed_method. Text values are restricted to the following list: none; direct_trap; empirical; theoretical; LVP (i.e.; Large volume pumps)
flux_mass, mg_m^-2_d^-1, Total dry mass flux of particulate matter (characterize methods with flux_sampling_method; etc.)
flux_P, mmol_m^-2_d^-1, Flux of total phosophorus (characterize methods with flux_sampling_method; etc.)
flux_particles, particles/m^2/d, Flux of particles (characterize methods with flux_sampling_method; etc.).
flux_Pb_210, dpm_m^-2_d^-1, Flux of lead 210 (characterize methods with flux_sampling_method; etc.)
flux_PC, mmol_m^-2_d^-1, Flux of Particulate Carbon (characterize methods with flux_sampling_method; etc.)
flux_PC_ATN, mmol_m^-2_d^-1, Flux of Particulate Carbon based on empirical calibration with flux_ATN (characterize methods with flux_sampling_method; etc.)
flux_PIC, mmol_m^-2_d^-1, Flux of Particulate Inorganic Carbon (characterize methods with flux_sampling_method; etc.)
flux_PN, mmol_m^-2_d^-1, Flux of Particulate Nitrogen (characterize methods with flux_sampling_method; etc.)
flux_Po_210, dpm_m^-2_d^-1, Flux of polonium 210 (characterize methods with flux_sampling_method; etc.)
flux_POC, mmol_m^-2_d^-1, Flux of Particulate Organic Carbon (characterize methods with flux_sampling_method; etc.)
flux_sampling_method, none, Flux_sampling_method must be included to characterize flux measurements in a SeaBASS file; along with flux_submethod; flux_calibration_method; and flux_sinking_speed_method. Text values are restricted to the following list: direct_trap; optical_trap; radiotracer; large_particles
flux_sinking_speed_method, none, Flux_sinking_speed_method must be included to characterize flux measurements in a SeaBASS file (if relevant; otherwise set to missing value); along with flux_sampling_method; flux_submethod; and flux_calibration_method. Text values are restricted to the following list: experimental; theoretical; inversion
flux_submethod, none, Flux_submethod must be included to characterize flux measurements in a SeaBASS file; along with flux_sampling_method; flux_calibration_method; and flux_sinking_speed_method. Text values are restricted to the following list: none; NBST (i.e.; Neutrally buoyant sediment trap); STT (i.e.; Surface tethered traps/sediment trap array); transmissometer; SnoCam (i.e.; Omand’s sediment trap camera); Th_234; Po_210; LVP (i.e.; Large volume pumps); UVP (i.e.; Underwater vision profiler); MOCNESS; gel_trap
flux_Th_234, dpm_m^-2_d^-1, Flux of Thorium 234 (characterize methods with flux_sampling_method; etc.)
Fm, unitless, Maximum fluorescence in darkness. Fast Repetition Rate Fluorescence measurement
FSC-A, arbunits, Area of the signal of light scattered in the forward direction from the laser interrogating particles (flow cytometry).
FSC-H, arbunits, Height of the signal of light scattered in the forward direction from the laser interrogating particles (flow cytometry).
FSCpar-H, arbunits, Height of the signal of light that has been aligned parallel to the original polarization of the laser interrogating particles (flow cytometry).
FSCperp-H, arbunits, Height of the signal of light that has been depolarized from the original polarization of the laser interrogating particles (flow cytometry).
Fuco, mg/m^3, HPLC Fucoxanthin
Fv_Fm, unitless, Maximum photochemical efficiency. Fast Repetition Rate Fluorescence measurement; commonly abbreviated as Fv/Fm
g, d^-1, Grazing Rate
g_herb, d^-1, Herbivorous Grazing Rate (i.e. Herbivore Induced Mortality)
geoform, none, Geoform (CMECS Units; Geoform Subcomponent; entry value should be text that does NOT contain the file's delimiter)
geoform_origin, none, Geoform origin (CMECS Units; Geoform Subcomponent; entry value should be text that does NOT contain the file's delimiter)
geoform_physiographic_setting, none, Geoform Component Physiographic Setting Subcomponent (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
geoform_tectonic_setting, none, Geoform Component Tectonic Subcomponent (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
geoform_type, none, Geoform type (CMECS Units; Geoform Subcomponent; entry value should be text that does NOT contain the file's delimiter)
GPP, mg/m^3/d, Gross Primary Productivity
Gyro, mg/m^3, HPLC Gyroxanthin-Diester
H2O_amps, amps, Peak intensity of H2O measured using EIMS
heading, degrees, platform's heading (e.g.; ship's); in degrees
Hex-fuco, mg/m^3, HPLC 19'-Hexanoyloxyfucoxanthin
Hex-kfuco, mg/m^3, HPLC 19'-Hexanoyloxy-4-ketofucoxanthin
hour, hh, Sample hour
hpl_id, none, HPL HPLC processing identification number
hplc_gsfc_id, none, NASA GSFC HPLC processing idenfication number (i.e. 'GSFC HPLC lab sampler code')
incubation_duration, hh, Incubation time
iso_C2H3N_H, ppbv, VOCC concentration of (13C2H3N)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
iso_C2H4O_H, ppbv, VOCC concentration of d3-acetaldehyde (C2HD3O)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
iso_C2H6S_H, ppbv, VOCC concentration of d3-dimethylsulfide (C2D3H3S)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
iso_C3H6O_H, ppbv, VOCC concentration of d6-acetone (C3D6O)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
iso_CH4O_H, ppbv, VOCC concentration of (13CH4O)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=.
It, degreesC, Instrument temperature
Kd, 1/m, Diffuse attenuation coefficient of Ed
Kl, 1/m, Diffuse attenuation coefficient of Lu
Knf, 1/m, Diffuse attenuation coefficient of natf
Kpar, 1/m, Diffuse attenuation coefficient of PAR
Ku, 1/m, Diffuse attenuation coefficient of Eu
lat, degrees, Sample latitude (decimal fractions; -90 to 90)
lat_end, degrees, Latitude where sampling ended (only needed for extended measurements; e.g.; multi-day integration measurements for drifting sediment traps)
lat_recovery, degrees, Latitude where instrumentation was recovered from the field (only needed for extended measurements; e.g.; multi-day integration measurements for sediment traps)
lat_resurface, degrees, Latitude where instrumentation resurfaced from a submerged deployment (e.g.; used for non-buoyant sediment traps)   
lat_start, degrees, Latitude where sampling started (only needed for extended measurements; e.g.; multi-day integration measurements for drifting sediment traps)
length_representation, um, Representation of length of the target detected within the ROI or largest mesh size for which the target could be retained; determined by means specified in the image processing method or protocol document.
lightlevel, %, Light sample was exposed to; relative to the ambient or experimental intensity
lon, degrees, Sample longitude (decimal fractions; -180 to 180)
lon_end, degrees, Longitude where sampling ended (only needed for extended measurements; e.g.; multi-day integration measurements for drifting sediment traps)
lon_recovery, degrees, Longitude where instrumentation was recovered from the field (only needed for extended measurements; e.g.; multi-day integration measurements for sediment traps)
lon_resurface, degrees, Longitude where instrumentation resurfaced from a submerged deployment (e.g.; used for non-buoyant sediment traps)   
lon_start, degrees, Longitude where sampling started (only needed for extended measurements; e.g.; multi-day integration measurements for drifting sediment traps)
LSi, mmol/m^3, Lithogenic silica
Lsky, uW/cm^2/nm/sr, Sky radiance
Lt, uW/cm^2/nm/sr, Total water radiance
Lu, uW/cm^2/nm/sr, Upwelling radiance
LuGND, volts, Dark current values for Lu sensor
Lut, mg/m^3, HPLC Lutein
Lw, uW/cm^2/nm/sr, Water leaving radiance
Lw_unc, uW/cm^2/nm/sr, Accumulated estimate of standard uncertainty associated with the derivation of water leaving radiance (Lw) via error propagation through the air-water interface.
Lwn, uW/cm^2/nm/sr, Normalized water leaving radiance (Lwn = Lw*F0/Es)
Lwnex, uW/cm^2/nm/sr, Exact normalized water leaving radiance ( e.g.; Morel et al. 2002 )
Lyco, mg/m^3, HPLC Lycopene
Me-chlide_a, mg/m^3, HPLC Methyl Chlorophyllide a
Me-chlide_b, mg/m^3, HPLC Methyl Chlorophyllide b
Mg_DVP, mg/m^3, HPLC Mg 2;4 divinyl pheoporphyrin a5 monomethyl ester
minute, mn, Sample minute
Monado, mg/m^3, HPLC Monadoxanthin
month, mo, Sample month
mPF, none, Microplankton proportion factor ([Fuco + Perid] / DP)
MUF, umol, Concentration of 4-Methylumbelliferone's fluorescent molecules without an associated substrate (used for the calibration curve in flow cytometry).
MUF-But, umol/L/hr, Rate of substrate cleavage for 4-Methylumbelliferyl butyrate
MUF-Glu, umol/L/hr, Rate of substrate cleavage for 4-Methylumbelliferyl beta-D-glucopyranoside
MUF-PO4, umol/L/hr, Rate of substrate cleavage for 4-Methylumbelliferyl phosphate
MV_Chl_a, mg/m^3, HPLC Monovinyl Chorophyll a
MV_Chl_b, mg/m^3, HPLC Monovinyl Chorophyll b
mz, unitless, Mass-to-charge ratio; used to describe proton-transfer-reaction time-of-flight mass spectrometer (PTR-TOF/MS) measurements
N2_amps, amps, Peak intensity of N2 measured using EIMS
N2_Ar_ratio, unitless, Ratio between N2 and Argon (Ar) peak intensities measured using EIMS
N2_fix, ug/m^3/d, Nitrogen Fixation Rates
N2_O2_ratio, unitless, Ratio between N2 and O2 peak intensities measured using EIMS
N2avg, s^-2, The mean squared buoyancy frequency (Brunt–Väisälä frequency) between the surface and measurement depth
nadir, degrees, Sensor nadir angle (the nadir is the downward facing viewing geometry; opposite the zenith)
nanoeukaryote, (see Field Name Suffixes table), Phytoplankton taxonomic label for nanoeukaryote. Use in combination with the supported suffixes in the Field Name Suffixes Table.
natf, nE/m^2/sr/s, natural fluorescence of chlorophyll a
NCCb, mmol/m^2/d, Net Benthic Community Calcification; expressed as the millimole production of CaCO3 per benthic area per day
NCP_O2_Ar_ratio_continuous, mmol/m^2/d, Net Community Productivity; expressed as the millimole production of O2 per area per day and calculated using the O2/Ar ratio from the ship’s flow-through seawater line by Equilibrator Inlet Mass Spectrometry (EIMS)
NCPb, mmol/m^2/d, Net Benthic Community Productivity; expressed as the millimole production of O2 per benthic area per day
Neo, mg/m^3, HPLC Neoxanthin
net_interval, m, net tow distance traveled
NH4, mmol/m^3, NH4
NO2, mmol/m^3, Nitrite
NO2_NO3, mmol/m^3, NO2 + NO3
no2ot, unitless, NO2 Optical Depth or NO2 Optical Thickness
NO3, mmol/m^3, Nitrate
nPF, none, Nanoplankton proportion factor ([Hex-fuco + But-fuco + Allo] / DP)
NPP, mg/m^3/d, Net Primary Productivity
nrb, photoelectrons/usec/shot, Normalized relative backscatter
O2_amps, amps, Peak intensity of O2 measured using EIMS
O2_Ar_ratio, unitless, Ratio between O2 and Argon (Ar) peak intensities measured using EIMS
o3ot, unitless, Ozone Optical Thickness or Ozone Optical Depth
oxygen, ml/L, Dissolved oxygen
oxygen_consumption_temcorr, uL/h, Oxygen consumption at the temperature that the organisms would have been at (temperature corrected)
oxygen_kg, umol/kg, Dissolved oxygen
oxygen_phase, degrees, Oxygen phase
oxygen_saturation, %, Percent oxygen saturation
Oz, dobson, Column Ozone
P-457, mg/m^3, HPLC P-457
PAR, uE/cm^2/s, PAR measured at the sea surface
PC, mmol/m^3, Concentration of Particulate Carbon
pCO2, uatm, Surface water partial pressure of carbon dioxide
pDrift, mbar, Pressure in the drift tube of the PTR-TOF/MS.
Perid, mg/m^3, HPLC Peridinin
pH, none, pH
PHAEO, mg/m^3, Total phaeopigment concentration
Phide_a, mg/m^3, HPLC Pheophorbide a
Phide_b, mg/m^3, HPLC Pheophorbide b
Phide_c, mg/m^3, HPLC Pheophorbide c
Phycocyanin, mg/m^3, Phycocyanin derived fluorometrically/spectrophotometrically
Phytin_a, mg/m^3, HPLC Pheophytin a
Phytin_b, mg/m^3, HPLC Pheophytin b
Phytin_c, mg/m^3, HPLC Pheophytin c
phyto_carbon, ug/L, Phytoplankton carbon concentration
Phytyl-chl_c, mg/m^3, HPLC Phytylated Chlorophyll c
PIC, mol/m^3, Particulate inorganic carbon
picoeukaryote, (see Field Name Suffixes table), Phytoplankton taxonomic label for picoeukaryote. Use in combination with the supported Field Name Suffixes Table.
PIM, mg/L, Suspended particulate inorganic matter
piston_velocity, m/d, Weighted piston velocity
pitch, degrees, Instrument pitch
pitch_Ed, degrees, Downwelling irradiance instrument pitch
pitch_Es, degrees, Downwelling surface irradiance instrument pitch
pitch_Lu, degrees, Upwelling radiance instrument pitch
PN, mg/m^3, Particulate nitrogen
PN_mmol, mmol/m^3, Particulate nitrogen
PO4, mmol/m^3, Phosphate
POC, mg/m^3, Particulate organic carbon
POC_cp, mg/m^3, Particulate organic carbon derived using particulate beam attenuation
POH, mg/m^3, Particulate organic hydrogen
POM, mg/L, Suspended particulate organic matter
PON, mg/m^3, Particulate organic nitrogen
PP, mgC/mgchla/hr, Primary productivity
PPC, mg/m^3, Photoprotective carotenoids (Allo + Diadino + Diato + Zeo + alpha-beta-Car)
PPC_Tcar, none, Ratio of PPC to Tcar
PPC_Tpg, none, Ratio of PPC to Tpg
pPF, none, Picoplankton proportion factor ([Zea + Tot_chl_b] / DP)
Pras, mg/m^3, HPLC Prasinoxanthin
pressure, dbar, Water pressure
pressure_atm, mbar, Atmospheric pressure
pressure_instrument, mbar, Pressure within the instrument
prochlorococcus, (see Field Name Suffixes table), Phytoplankton taxonomic label for prochlorococcus. Use in combination with the supported Field Name Suffixes listed in the above table; relating to taxonomic types.
profile, none, Profile id or number. Positive values are used for upward profiles; and negative values for downward profiles.
PSC, mg/m^3, Photosynthetic carotenoids (But-fuco + Fuco + Hex-fuco + Perid)
PSC_Tcar, none, Ratio of PSC to Tcar
PSD, uL/L, Particle Size Distribution. Must be used in conjunction with a suffix to specify sizes; e.g.; PSD_80.5size (see _###size in table of field name modifiers.)
PSD_DNSD, number/m^3/um, Differential number size distribution. Must be used in conjunction with a suffix to specify sizes; e.g.; PSD_DNSD_80.5umsize (see _###umsize in table of field name modifiers).  Dataset should include the /PSD_bin_size_method and /PSD_bin_size_boundaries metadata headers.
PSD_DVSD, uL/m^3/um, Differential volume size distribution. Must be used in conjunction with a suffix to specify sizes; e.g.; PSD_DVSD_80.5umsize (see _###umsize in table of field name modifiers).  Dataset should include the /PSD_bin_size_method and /PSD_bin_size_boundaries metadata headers.
PSP, mg/m^3, Photosynthetic pigments (PSC + Tchl)
PSP_Tpg, none, Ratio of PSP to Tpg
PTP, mmol/m^3, Concentration of total particulate phosphorus
pulse_width, seconds, Time duration that the primary trigger channel exceeded the width measurement threshold during an event (flow cytometry). Scientific notation is accepted.
pvel, m/s, Profiler velocity
Pyrophide_a, mg/m^3, HPLC Pyropheophorbide a
Pyrophytin_a, mg/m^3, HPLC Pyropheophytin a
Pyrophytin_b, mg/m^3, HPLC Pyropheophytin b
Pyrophytin_c, mg/m^3, HPLC Pyropheophytin c
Q, sr, Eu / Lu (equal to pi in diffuse water)
quality, none, Analyst-specific data quality flag. A definition of the quality flags should be provided as metadata header comments and within accompanying documentation files.
R, unitless, Irradiance reflectance (Eu / Ed)
R2R_Event, none, Rolling Deck to Repository (R2R) Unique sample event number
rate_13C_uptake_bottle, mol/L/d;mol_L^-1_d^-1, Primary productivity determined using 13C. This field should inclute the experiment time (incubation time) "_###hr".
rate_15N_uptake_bottle, mol/L/d;mol_L^-1_d^-1, Rates of nitrogen uptake. This field should inclute the experiment time (incubation time) "_###hr".
rate_diff_02_dark_incub, mmol/m^3/d, O2 drawdown rate
rate_diff_C_dark_incub, mmol/m^3/d, C drawdown rate
rate_diff_O2_corrcoef, none, O2 drawdown rate correlation coefficient
rate_nitrification, nmol/L/d, Nitrification rate
rate_production_DOC_inc, mg/mg_body_C/d, Mass specific (calculated as mg dry mass carbon per individual) excreted dissolved organic carbon per day
rate_respiration_C_ind, mg/mg_body_C/d, Oxygen consumption rate per organism calculated as the change in carbon concentration (in mg body C assuming 40% zooplankton dry weight was carbon)
rate_respiration_carbon_zoop, mg/m^2/d, Zooplankton raspiration rates in mg of Carbon/m^2/d
rate_respiration_O2_ind, umol/ind/h, Oxygen consumption rate per organism calculated as the change in oxygen concentration (umol O2 per individual per hour)
ratio, unitless, Used for specific ratios. Please contact SeaBASS before using it.
Rb, unitless, Benthic irradiance reflectance (Lambertian equivalence reflectance)
RelAbundance, %, Percent cell abundance of a specific phytoplankton taxonomic type relative to all observed cells.
RelAz, degrees, Sensor azimuth angle relative to the solar plane
Rf, uW/cm^2/nm/sr, Raman fluorescence (may be used in combination with suffixes _ex### and/or _em###; like so: Rf_ex###_em###; ex = excitation wavelength; em = emission wavelength)
rho, unitless   , Surface reflectance
Rl, 1/sr, Radiance reflectance (Lu/Ed)
RNA, mg/m^3, RNA (Ribonucleid Acid) concentration within a water volume
roll, degrees, Instrument roll
roll_Ed, degrees, Downwelling irradiance Instrument roll
roll_Es, degrees, Downwelling surface irradiance instrument roll
roll_Lu, degrees, Upwelling radiance instrument roll
rot, unitless, Rayleigh Optical Depth or Rayleigh Optical Thickness
Rpi, unitless, Radiance reflectance with pi (pi*Lu/Ed)
rrna_gene, none, Small subunit ribosomes targeted for sequencing (e.g.; 16S or 18S)
Rrs, 1/sr, Remote sensing reflectance (Lw/Ed)
Rrs_unc, 1/sr, Accumulated estimate of standard uncertainty associated with the derivation of remote sensing reflectance (Rrs) via propagation of radiance and irradiance errors through the remote sensing reflectance computations.
S_ad, none, Slope of non-algal detritus absorption spectra
S_ag, none, Slope of gelbstoff absorption spectra. Please include the wavelength range used for the calculation following this format as an example: s_ag_300nmmin_600_nmmax. If only one data value per dataset; please use the following header and format: /s_ag=s_ag_#nmmin_#nmamax:value; where # is wavelength and value is your data value.
sal, PSU, Salinity
sample, none, Sample number
SAZ, degrees, Solar azimuth angle
scientificName_automated, none, A scientific name from a recognized taxonomic reference database (e.g.; WoRMS; AlgaeBase) at the lowest level that matches the data provider's category for an automated classification paired to a scientificNameID. Generally; the ROI corresponds to an occurrence assigned to a single taxonomic name; e.g.; Karenia brevis
scientificName_manual, none, A scientific name from a recognized taxonomic reference database (e.g.; World Register of Marine Species; AlgaeBase) at the lowest level that matches the data provider's category; for a manual identification matched to scientificNameID. Generally; the ROI corresponds to an occurrence assigned to a single taxonomic name.
scientificNameID_automated, none, A life science identifier (LSID) from a recognized taxonomic reference database (e.g.; WoRMS; AlgaeBase) at the lowest level that matches the data provider's category for an automated classification. e.g.; urn:lsid:marinespecies.org:taxname:233015 where ‘urn:lsid’ indicates the ID that is specific to life science data and is used for all files; marinespecies.org is the url for the reference database WoRMS; and the namespace ‘taxname’ informs the user that the following number represents a unique numerical identifier or taxon identifier in WoRMS. 233015 represents the taxon identifier (AphiaID) in WoRMS for the dinoflagellate species Karenia brevis.
scientificNameID_manual, none, A scientific name from a recognized taxonomic reference database (e.g.; World Register of Marine Species; AlgaeBase) at the lowest level that matches the data provider's category; for a manual identification matched to scientificNameID. Generally; the ROI corresponds to an occurrence assigned to a single taxonomic name.
sdy, ddd, Sequential day of year
second, ss, Sample second
SenZ, degrees, Sensor zenith angle
sig, mV, Stregth of the raw signal of the sunphotometer
sigma_PSII, angstrom^2, Effective absorption cross-section of photosystem II in darkness
sigma_theta, kg/m^3, Potential density - 1000 kg/m3
sigmaT, kg/m^3, Density - 1000 kg/m3
SiO4, mmol/m^3, Silicic Acid / "Dissolved Silica"
Siphn, mg/m^3, HPLC Siphonein
Siphx, mg/m^3, HPLC Siphonaxanthin
SN, none, Instrument serial number
speed_f_w, m/s, Speed in the forward direction; relative to water
SPM, mg/L, Total suspended particulate matter
SSC-A, arbunits, Area of the signal of light side scattered from the laser interrogating particles (flow cytometry).
SSC-H, arbunits, Height of the signal of light side scattered from the laser interrogating particles (flow cytometry).
SST, degreesC, Sea surface temperature
station, none, Sample station
station_alt_id, none, Alternate sample station identifier (use ONLY if station has already been used as a field name)
stimf, volts, Stimulated fluorescence; nominally of chlorophyll a. The suffixes _ex### and _em### may be used to specify wavelengths like so: stimf_ex###_em###; ex = excitation wavelength; em = emission wavelength). Related field: Chl_stimf
stimf_counts, counts, Stimulated fluorescence (see "stimf") expressed in units of counts instead of volts
substrate_class, none, Substrate class; Substrate Component level 2 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
substrate_group, none, Substrate group; Substrate Component level 4 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
substrate_origin, none, Substrate origin; Substrate Component level 1 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
substrate_subclass, none, Substrate subclass; Substrate Component level 3 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
substrate_subgroup, none, Substrate subgroup; Substrate Component level 5 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
Sv, dB, Time dependent range and volume backscattering (dB relative to m^-1). Acoustics Data. [Speak with SeaBASS staff before submitting this type of data]
synechococcus, (see Field Name Suffixes table), Phytoplankton taxonomic label for synechococcus. Use in combination with the supported Field Name Suffixes listed in the above table; relating to taxonomic types.
SZ, m, Secchi disk depth
SZA, degrees, Solar zenith angle
Tacc, mg/m^3, Total accessory pigments (PPC + PSC + Tot_Chl_b + Tot_Chl_c)
Tacc_Tchla, none, Ratio of Tacc to Tot_Chl_a
TauAv, ns, Fluorescence kinetics decay time (i.e.; fluorescence lifetime of the excited photosynthetic unit)
Tcar, mg/m^3, Total carotenoids (PPC + PSC)
Tchl, mg/m^3, Tot_Chl_a + Tot_Chl_b + Tot_Chl_c
TChl_Tcar, none, Ratio of Tchl to Tcar
Tchla_Tpg, none, Ratio of Tot_chl_a to Tpg
TDN, mmol/m^3, Total dissolved nitrogen (per volume)
TDN_kg, umol/kg, Total dissolved nitrogen (per mass)
Tdrift, degreesC, Temperature in the drift tube of the PTR-TOF/MS.
TEP_bottle,  ug_Gxan_equiv/L, Transparent Exopolymer Particles (TEP) in the water (collected via Niskin bottles)
TEP_MSC, ug_Gxan_equiv/L, Transparent Exopolymer Particles (TEP) in the water (collected via Marine Snow Catcher)
tilt, degrees, Instrument tilt
tilt_Ed, degrees, Downwelling irradiance instrument tilt
tilt_Es, degrees, Downwelling surface irradiance instrument tilt
tilt_Lu, degrees, Upwelling radiance instrument tilt
time, hh:mm:ss, Sample time [GMT]
time_end, hh:mm:ss, Time measurements stopped (only needed for extended measurements; e.g.; multi-day integration measurements for sediment traps; also see "date_end") [GMT]
time_processed, hh:mm:ss, Time the sample was processed [GMT]
time_recovery, hh:mm:ss, Time instrumentation was recovered from the field (only needed for extended measurements; e.g.; multi-day integration measurements for sediment traps) [GMT]
time_resurface, hh:mm:ss, Time instrumentation resurfaced from a submerged deployment (e.g.; used for non-buoyant sediment traps) [GMT]
time_start, hh:mm:ss, Time sampling began (only needed for extended measurements; e.g.; multi-day integration measurements for sediment traps) [GMT]
TOC, umol/kg, Total Organic Carbon (per mass)
TOC_L, umol/L, Total Organic Carbon (per volume)
Tot_Chl_a, mg/m^3, HPLC DV_Chl_a + MV_Chl_a + Chlide_a + Chl_a_allom + Chl_a_prime
Tot_Chl_b, mg/m^3, HPLC DV_Chl_b + MV_Chl_b
Tot_Chl_c, mg/m^3, HPLC chl_c1 + chl_c2 (i.e.; chl_c1c2) + chl_c3
total_alkalinity, umol/kg, Total alkalinity
Total_C, mg/m^3, Total carbon
total_NO2, Dobson, Atmospheric total nitrate (NO2)
Total_precipitable_water, cm, Total precipitable water
Tpg, mg/m^3, Total pigment concentration
trans, %, Percent transmission
turbidity, NTU, Turbidity
u, d^-1, Growth rate (i.e.; µ or mu)
u_ph, d^-1, Growth rate of phytoplankton
u_zoo, d^-1, Growth rate of zooplankton
Urea, mmol/m^3, Urea
Vauch, mg/m^3, HPLC Vaucheriaxanthin-ester
VelEast, m/s, ADP Velocity East
VelNorth, m/s, ADP Velocity North
VelUp, m/s, ADP Velocity Up
Viola, mg/m^3, HPLC Violaxanthin
VOCair, ppbv, Concenctration of Volatile Organic Carbon (VOC) compounds in air measured via a proton-transfer-reaction time-of-flight mass spectrometer (PTR-TOF/MS)
volfilt, L, Volume filtered
volume, L, Volume used in experiment
VSF, 1/m/sr, Total volume scattering function (VSF### or VSF###_YYYang; where YYY is collection angle). Also called beta.
VSFg, 1/m/sr, Gelbstoff volume scattering function; i.e.; VSFg = VSFw - VSF(pure water; salinity; and temperature) (VSFg### or VSFp###_YYYang; where YYY is collection angle). Also called beta.
VSFp, 1/m/sr, Particulate volume scattering function i.e.; VSFp = VSF - VSFw (VSFp### or VSFp###_YYYang; where YYY is collection angle). Also called beta.
VSFw, 1/m/sr, Filtered seawater volume scattering function plus VSF sal & temp contributions; i.e.; VSFw = VSF - VSFp (VSFw### or VSFw###_YYYang; where YYY is collection angle). Also called beta.
water_column_biogeochemical_feature, none, Water Column Biogeochemical Feature Subcomponent (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
water_column_hydroform, none, Water Column Hydroform Subcomponent level 2 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
water_column_hydroform_class, none, Water Column Hydroform Subcomponent level 1 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
water_column_hydroform_type, none, Water Column Hydroform Subcomponent level 3 (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
water_column_layer, none, Water Column Layer Subcomponent (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
water_column_salinity, none, Water Column Salinity Subcomponent (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
water_column_temperature, none, Water Column Temperature Subcomponent (CMECS Units; entry value should be text that does NOT contain the file's delimiter)
water_depth, m, The water (bottom) depth where the data were collected
waveht, m, Wave height
wavelength, nm, Wavelength of measurement
wdir, degrees, Wind direction; described in degrees from north; increasing clockwise
weight_dry, mg, Sample dry weight
weight_protein_community, mg/m^3, Weight of the protein in the mesozooplankton sample
weight_protein_sample, mg/sample, Weight of the protein in the whole mesozooplankton community
weight_wet, mg, Sample wet weight
width_representation, um, Representation of width of the target detected within the ROI or smallest mesh size through which the target could pass; determined by means specified in the image processing method or protocol document.
wind, m/s, Wind speed
Wt, degreesC, Water temperature
wvot, unitless, Water vapor optical thickness or water vapor optical density
Wvp, cm, Water vapor
year, yyyy, Sample year
Z_90, m, Depth of the first optical layer (37% light level)
Z_DCM, m, Depth of the deep chlorophyll maximum
Z_Eu, m, Depth of the euphotic layer
Z_MLD, m, Depth of the mixed layer
Z_XML, m, Depth of the active mixing layer
Zea, mg/m^3, HPLC Zeaxanthin
zoop_biomass_dry, mg/m^3, Zooplankton biomass dry weight
zoop_biomass_wet, mg/m^3, Zooplankton biomass wet weight
 
```