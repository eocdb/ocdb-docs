# Standard field names and units

Standard fields table below shows the list of valid field names and units to be used both when submitting measurements and querying the Database. 
In order to guarantee interoperability with NASA SeaBASS Database, [SeaBASS Standard Fields and Units](https://seabass.gsfc.nasa.gov/wiki/stdfields) have been reported here, together with OCDB dedicated variables. The table it is also constantly updated with new fields, whenever needed. 


```eval_rst

.. csv-table:: Standard fields
   :header: Field_Name,Units,Description
   :widths: 20, 10, 70
   :stub-columns: 1
   
   a, 1/m, Total absorption coefficient (aw + ap + ag) 
   a*ph, m^2/mg, Chlorophyll a specific absorption coefficient 
   a*srfa, m^2/mg, Specific absorption coefficient of Suwanee River Fulvic Acid standard 
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
   abundance, none," Number of cells observed (to specify a particular taxonomic type, see ""_abun"" in Table of Field Name Suffixes) "
   ad, 1/m, Absorption coefficient of non-algal detritus 
   ad_unc, 1/m," Accumulated estimate of standard uncertainty associated with the derivation of the absorption coefficient of non-algal detritus (ad) via error propagation through the absorption equation. See section 5.3.4 of IOCCG's ""Volume 1: Inherent Optical Property Measurements and Protocols: Absorption Coefficient"" (2018). "
   adg, 1/m, Absorption coefficient of non-algal detritus + Gelbstoff (ad + ag) 
   ag, 1/m, Absorption coefficient of Gelbstoff 
   agp, 1/m, Absorption coefficient of Gelbstoff + particles (ag + ap) 
   Allo, mg/m^3, HPLC Alloxanthin 
   alpha-beta-Car, mg/m^3," HPLC Alpha (Beta,epsilon) + Beta (Beta,beta) Carotenes "
   altitude, m, Altitude above sea level 
   am, unitless, Airmass 
   AMC, umol, Concentration of 7-Amino-4-methylcoumarin's fluorescent molecules without an associated substrate (used for the calibration curve in flow cytometry). 
   AMC-Leu, umol/L/hr, Rate of substrate cleavage for L-Leucine-7-amido-4-methylcoumarin hydrochloride 
   angstrom, unitless, Angstrom exponent 
   Anth, mg/m^3, HPLC Antheraxanthin 
   AOT, unitless, Aerosol Optical Thickness (sometimes referred to as tau or taua) 
   ap, 1/m, Absorption coefficient of particles (ad + aph) 
   ap_unc, 1/m," Accumulated estimate of standard uncertainty associated with the derivation of the absorption coefficient of particles (ap) via error propagation through the absorption equation. See section 5.3.4 of IOCCG's ""Volume 1: Inherent Optical Property Measurements and Protocols: Absorption Coefficient"" (2018). "
   aph, 1/m, Absorption coefficient of phytoplankton 
   aph_unc, 1/m," Accumulated estimate of standard uncertainty associated with the derivation of the absorption coefficient of phytoplankton (aph) via error propagation through the absorption equation. See section 5.3.4 of IOCCG's "" Volume 1: Inherent Optical Property Measurements and Protocols: Absorption Coefficient"" (2018). "
   asrfa, 1/m, Absorption coefficient of Suwanee River Fulvic Acid standard 
   associated_file_types, none," File type of an associated file. Please contact SeaBASS staff before using this field to verify that your file type is supported. Valid entries for this field are: DNA-FASTQ, DNA-FASTA (for files relating to DNA analysis), BENTHIC (for images relating to benthic type and cover), and PLANKTONIC (for images relating to flow cam imagery or phytoplankton taxonomic types). If multiple entries are applicable, separate them with the pipe character!"
   associated_files, none," File name of an associated file. Must be used with associated_file_type. Please include the file suffix in the entry. If multiple entries are applicable, separate them with the pipe character: "
   Asta, mg/m^3, HPLC Astaxanthin 
   At, degreesC, Air temperature 
   aw, 1/m, Absorption coefficient of water 
   b, 1/m, Total scattering coefficient (bw + bp) 
   bact_abun, cells/L, Bacterioplankton abundance 
   bactP, pmol/L/hr, Bacterioplankton production 
   bb, 1/m, Total backscattering coefficient (bbw + bbp) 
   bbp, 1/m, Backscattering coefficient of particles 
   bbp_bp, unitless, Ratio of the backscattering coefficient of particles (bbp) to the total backscattering coefficient (bp) 
   bbw, 1/m, Backscattering coefficient of water 
   BChl_a, mg/m^3, HPLC Bacteriochlorophyll a 
   benthic_type, none, Description of the benthic seafloor community or substrate. 
   beta-beta-Car, mg/m^3," HPLC Beta-Carotene (Beta,beta-Carotene) "
   beta-epi-Car, mg/m^3," HPLC Alpha-Carotene (Beta,epsilon-Carotene) "
   beta-psi-Car, mg/m^3," HPLC Gamma-Carotene (Beta,psi-Carotene) "
   bin_depth, m, Nominal or center depth for each data bin 
   bincount, none, Number of records averaged into a bin or reported measurement 
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
   cdmf, volts," CDOM fluorescence (may be used in combination with suffixes _ex### and/or _em###, like so: cdmf_ex###_em###; ex = excitation wavelength; em = emission wavelength) "
   cdom, mg/m^3, Concentration of chromophoric dissolved organic matter 
   cg, 1/m, Attenuation coefficient of Gelbstoff 
   cgp, 1/m, Attenuation coefficient of Gelbstoff + particles (c - cw = agp + bp) 
   CH4O_H, ppbv, VOCC concentration of (CH4O)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=. 
   CH4S_H, ppbv, VOCC concentrations of (CH4S)H+ in the air evolved from the experimental chambers that are measured by the PTR-TOF/MS. Use with headers /chemical_formula= and /mass_to_charge=. 
   Chl, mg/m^3," Chlorophyll a derived fluorometrically/spectrophotometrically (e.g., ""extracted"" Chl) "
   Chl_a, mg/m^3, HPLC Chlorophyll a (MV_Chl_a plus allomers and epimers) 
   Chl_a_allom, mg/m^3, HPLC Chlorophyll a allomers 
   Chl_a_prime, mg/m^3, HPLC Chlorophyll a epimer 
   Chl_b, mg/m^3, HPLC Chlorophyll b 
   Chl_c, mg/m^3, HPLC Chlorophyll c 
   Chl_c1, mg/m^3, HPLC Chlorophyll c1 
   Chl_c1c2, mg/m^3, HPLC Chlorophyll c1 + c2 + Mg_DVP 
   Chl_c2, mg/m^3, HPLC Chlorophyll c2 
   Chl_c3, mg/m^3, HPLC Chlorophyll c3 
   Chl_experiment, mg/m^3," Chlorophyll a derived via experiment, or experimental methods. See specific documentation for more information. "
   Chlide_a, mg/m^3, HPLC Chlorophyllide a 
   Chlide_b, mg/m^3, HPLC Chlorophyllide b 
   chors_id, none, CHORS HPLC processing identification number 
   cloud, %, Percent cloud cover 
   cnw, 1/m, Attenuation coefficient of Gelbstoff + particles (obsolete; see cgp) 
   cond, mmho/cm, Conductivity 
   cp, 1/m, Beam attenuation coefficient of particles (ap + bp) 
   cp_gamma, unitless, Particulate beam attenuation spectra's slope 
   Croco, mg/m^3, HPLC Crocoxanthin 
   cw, 1/m, Beam attenuation coefficient of water (aw + bw) 
   cycle, none, Incrementing counter describing the sampling interval of the instrument. Relevant to the PTR-TOF/MS. 
   date, yyyymmdd, Sample date 
   date_processed, yyyymmdd, Date the sample was processed 
   day, dd, Sample day 
   depth, m, Depth of measurement 
   dewpoint, degreesC, Dew point temperature 
   Diadchr, mg/m^3, HPLC Diadinochrome 
   Diadino, mg/m^3, HPLC Diadinoxanthin 
   Diato, mg/m^3, HPLC Diatoxanthin 
   DIC, umol/kg, Dissolved inorganic carbon (per kg) 
   Dino, mg/m^3, HPLC Dinoxanthin 
   DMSA, ppt, Concentration of dimethyl sulfide (DMS) in the atmosphere 
   DMSSW, nmol/L, Concentration of dimethyl sulfide (DMS) in sea water 
   DNA, mg/m^3, DNA (DeoxyriboNucleic Acid) concentration within a water volume 
   DOC, umol/kg, Dissolved organic carbon (per kg) 
   DP, mg/m^3, Total diagnostic pigments (PSC + Allo + Zea + Tot_Chl_b) 
   DV_Chl_a, mg/m^3, HPLC Divinyl Chorophyll a 
   DV_Chl_b, mg/m^3, HPLC Divinyl Chorophyll b 
   Echin, mg/m^3, HPLC Echinenone 
   Ed, uW/cm^2/nm, Downwelling irradiance 
   EdGND, volts, Dark current values for Ed sensor 
   elapsed_time, seconds, Elapsed time 
   Elw, uW/cm^2," Downwelling irradiance over the infrared spectrum, 3 to 40 um "
   Epar, uE/cm^2/s, Profiled PAR 
   epi-epi-Car, mg/m^3," HPLC Epsilon-Carotene (Epsilon,epsilon-Carotene) "
   Es, uW/cm^2/nm, Downwelling surface irradiance 
   EsGND, volts, Dark current values for Es sensor 
   Esky, uW/cm^2/nm, Downwelling sky irradiance 
   Esun, uW/cm^2/nm, Downwelling sun irradiance (direct normal solar irradiance) 
   Esw, uW/cm^2," Downwelling irradiance over the solar spectrum, 0.3 to 3 um "
   Et-8-carot, mg/m^3, HPLC Ethyl-apo-8'-carotene 
   Et-chlide_a, mg/m^3, HPLC Ethyl Chlorophyllide a 
   Et-chlide_b, mg/m^3, HPLC Ethyl Chlorophyllide b 
   Eu, uW/cm^2/nm, Upwelling irradiance 
   EuGND, volts, Dark current values for Eu sensor 
   EuPAR, uE/cm^2/s, Profiled upwelling PAR 
   F0, uW/cm^2/nm, Extraterrestrial solar irradiance 
   F-initial, unitless," Minimum fluorescence in darkness. Fast Repetition Rate Fluorescence measurement, commonly abbreviated as F0 "
   Fm, unitless, Maximum fluorescence in darkness. Fast Repetition Rate Fluorescence measurement 
   Fuco, mg/m^3, HPLC Fucoxanthin 
   Fv_Fm, unitless," Maximum photochemical efficiency. Fast Repetition Rate Fluorescence measurement, commonly abbreviated as Fv/Fm "
   g, d^-1, Grazing Rate 
   g_herb, d^-1," Herbivorous Grazing Rate (i.e., Herbivore Induced Mortality) "
   Gyro, mg/m^3, HPLC Gyroxanthin-Diester 
   heading, degrees," platform's heading (e.g., ship's), in degrees "
   Hex-fuco, mg/m^3, HPLC 19'-Hexanoyloxyfucoxanthin 
   Hex-kfuco, mg/m^3, HPLC 19'-Hexanoyloxy-4-ketofucoxanthin 
   hour, hh, Sample hour 
   hpl_id, none, HPL HPLC processing identification number 
   hplc_gsfc_id, none, NASA GSFC HPLC processing idenfication number (i.e. 'GSFC HPLC lab sampler code') 
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
   lat, degrees, Sample latitude 
   lightlevel, %," Light sample was exposed to, relative to the ambient or experimental intensity "
   lon, degrees, Sample longitude 
   LSi, mmol/m^3, Lithogenic silica 
   Lsky, uW/cm^2/nm/sr, Sky radiance 
   Lt, uW/cm^2/nm/sr, Total water radiance 
   Lu, uW/cm^2/nm/sr, Upwelling radiance 
   LuGND, volts, Dark current values for Lu sensor 
   Lut, mg/m^3, HPLC Lutein 
   Lw, uW/cm^2/nm/sr, Water leaving radiance 
   Lw_unc, uW/cm^2/nm/sr, Accumulated estimate of standard uncertainty associated with the derivation of water leaving radiance (Lw) via error propagation through the air-water interface.
   Lwn, uW/cm^2/nm/sr, Normalized water leaving radiance ( Lwn = Lw * F0 / Es ) 
   Lwnex, uW/cm^2/nm/sr," Exact normalized water leaving radiance ( e.g., Morel et al. 2002 ) "
   Lyco, mg/m^3, HPLC Lycopene 
   Me-chlide_a, mg/m^3, HPLC Methyl Chlorophyllide a 
   Me-chlide_b, mg/m^3, HPLC Methyl Chlorophyllide b 
   Mg_DVP, mg/m^3," HPLC Mg 2,4 divinyl pheoporphyrin a5 monomethyl ester "
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
   mz, unitless," Mass-to-charge ratio, used to describe proton-transfer-reaction time-of-flight mass spectrometer (PTR-TOF/MS) measurements "
   N2_fix, ug/m^3/d, Nitrogen Fixation Rates 
   nadir, degrees," Sensor nadir angle (the nadir is the downward facing viewing geometry, opposite the zenith) "
   nanoeukaryote, (see Field Name Suffixes table), Phytoplankton taxonomic label for nanoeukaryote. Use in combination with the supported suffixes in the Field Name Suffixes Table. 
   natf, nE/m^2/sr/s, natural fluorescence of chlorophyll a 
   NCCb, mmol/m^2/d," Net Benthic Community Calcification, expressed as the millimole production of CaCO3 per benthic area per day "
   NCPb, mmol/m^2/d," Net Benthic Community Productivity, expressed as the millimole production of O2 per benthic area per day "
   Neo, mg/m^3, HPLC Neoxanthin 
   NH4, mmol/m^3, NH4 
   NO2, mmol/m^3, Nitrite 
   NO2_NO3, mmol/m^3, NO2 + NO3 
   NO3, mmol/m^3, Nitrate 
   nPF, none, Nanoplankton proportion factor ([Hex-fuco + But-fuco + Allo] / DP) 
   NPP, mg/m^3/d, Net Primary Productivity 
   nrb, photoelectrons/usec/shot, Normalized relative backscatter 
   oxygen, ml/L, Dissolved oxygen 
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
   Phytin_a, mg/m^3, HPLC Pheophytin a 
   Phytin_b, mg/m^3, HPLC Pheophytin b 
   Phytin_c, mg/m^3, HPLC Pheophytin c 
   phyto_carbon, ug/L, Phytoplankton carbon concentration 
   Phytyl-chl_c, mg/m^3, HPLC Phytylated Chlorophyll c 
   PIC, mol/m^3, Particulate inorganic carbon 
   picoeukaryote, (see Field Name Suffixes table), Phytoplankton taxonomic label for picoeukaryote. Use in combination with the supported Field Name Suffixes Table. 
   PIM, mg/L, Suspended particulate inorganic matter 
   pitch, degrees, Instrument pitch 
   PN, mg/m^3, Particulate nitrogen 
   PO4, mmol/m^3, Phosphate 
   POC, mg/m^3, Particulate organic carbon 
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
   prochlorococcus, (see Field Name Suffixes table)," Phytoplankton taxonomic label for prochlorococcus. Use in combination with the supported Field Name Suffixes listed in the above table, relating to taxonomic types. "
   PSC, mg/m^3, Photosynthetic carotenoids (But-fuco + Fuco + Hex-fuco + Perid) 
   PSC_Tcar, none, Ratio of PSC to Tcar 
   PSD, uL/L," Particle Size Distribution. Must be used in conjunction with a suffix to specify sizes, e.g., PSD_80.5size (see _###size in table of field name modifiers.) "
   PSP, mg/m^3, Photosynthetic pigments (PSC + Tchl) 
   PSP_Tpg, none, Ratio of PSP to Tpg 
   pulse_width, seconds, Time duration that the primary trigger channel exceeded the width measurement threshold during an event (flow cytometry). Scientific notation is accepted. 
   pvel, m/s, Profiler velocity 
   Pyrophide_a, mg/m^3, HPLC Pyropheophorbide a 
   Pyrophytin_a, mg/m^3, HPLC Pyropheophytin a 
   Pyrophytin_b, mg/m^3, HPLC Pyropheophytin b 
   Pyrophytin_c, mg/m^3, HPLC Pyropheophytin c 
   Q, sr, Eu / Lu (equal to pi in diffuse water) 
   quality, none, Analyst-specific data quality flag 
   R, unitless, Irradiance reflectance (Eu / Ed) 
   RelAbundance, %, Percent cell abundance of a specific phytoplankton taxonomic type relative to all observed cells. 
   RelAz, degrees, Sensor azimuth angle relative to the solar plane 
   Rf, uW/cm^2/nm/sr," Raman fluorescence (may be used in combination with suffixes _ex### and/or _em###, like so: Rf_ex###_em###; ex = excitation wavelength; em = emission wavelength) "
   Rl, 1/sr, Radiance reflectance (Lu / Ed) 
   roll, degrees, Instrument roll 
   Rpi, unitless, Radiance reflectance with pi (pi * Lu / Ed) 
   Rrs, 1/sr, Remote sensing reflectance (Lw / Ed) 
   S_ad, none, Slope of non-algal detritus absorption spectra 
   S_ag, none, Slope of gelbstoff absorption spectra 
   sal, PSU, Salinity 
   sample, none, Sample number 
   SAZ, degrees, Solar azimuth angle 
   sdy, ddd, Sequential day of year 
   second, ss, Sample second 
   SenZ, degrees, Sensor zenith angle 
   sig, mV, Stregth of the raw signal of the sunphotometer 
   sigma_PSII, angstrom^2, Effective absorption cross-section of photosystem II in darkness 
   sigma_theta, kg/m^3, Potential density - 1000 kg/m3 
   sigmaT, kg/m^3, Density - 1000 kg/m3 
   SiO4, mmol/m^3," Silicic Acid / ""Dissolved Silica"" "
   Siphn, mg/m^3, HPLC Siphonein 
   Siphx, mg/m^3, HPLC Siphonaxanthin 
   SN, none, Instrument serial number 
   speed_f_w, m/s," Speed in the forward direction, relative to water "
   SPM, mg/L, Total suspended particulate matter 
   SST, degreesC, Sea surface temperature 
   station, none, Sample station 
   station_alt_id, none, Alternate sample station identifier (use ONLY if station has already been used as a field name) 
   stimf, volts," Stimulated fluorescence, nominally of chlorophyll a. The suffixes _ex### and _em### may be used to specify wavelengths like so: stimf_ex###_em###; ex = excitation wavelength; em = emission wavelength). Related field: Chl_stimf "
   synechococcus, (see Field Name Suffixes table)," Phytoplankton taxonomic label for synechococcus. Use in combination with the supported Field Name Suffixes listed in the above table, relating to taxonomic types. "
   SZ, m, Secchi disk depth 
   SZA, degrees, Solar zenith angle 
   Tacc, mg/m^3, Total accessory pigments (PPC + PSC + Tot_Chl_b + Tot_Chl_c) 
   Tacc_Tchla, none, Ratio of Tacc to Tot_Chl_a 
   Tcar, mg/m^3, Total carotenoids (PPC + PSC) 
   Tchl, mg/m^3, Tot_Chl_a + Tot_Chl_b + Tot_Chl_c 
   TChl_Tcar, none, Ratio of Tchl to Tcar 
   Tchla_Tpg, none, Ratio of Tot_chl_a to Tpg 
   TDN, mmol/m^3, Total dissolved nitrogen 
   Tdrift, degreesC, Temperature in the drift tube of the PTR-TOF/MS. 
   tilt, degrees, Instrument tilt 
   time, hh:mm:ss, Sample time 
   time_processed, hh:mm:ss, Time the sample was processed 
   Tot_Chl_a, mg/m^3, HPLC DV_Chl_a + MV_Chl_a + Chlide_a + Chl_a_allom + Chl_a_prime 
   Tot_Chl_b, mg/m^3, HPLC DV_Chl_b + MV_Chl_b 
   Tot_Chl_c, mg/m^3," HPLC chl_c1 + chl_c2 (i.e., chl_c1c2) + chl_c3 "
   Tpg, mg/m^3, Total pigment concentration 
   trans, %, Percent transmission 
   turbidity, NTU, Turbidity 
   u, d^-1," Growth rate (i.e., µ or mu) "
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
   VSF, 1/m/sr," Total volume scattering function (VSF### or VSF###_YYYang, where YYY is collection angle). Also called beta. "
   VSFg, 1/m/sr," Gelbstoff volume scattering function, i.e., VSFg = VSFw - VSF(pure water, salinity, and temperature) (VSFg### or VSFp###_YYYang, where YYY is collection angle). Also called beta. "
   VSFp, 1/m/sr," Particulate volume scattering function i.e., VSFp = VSF - VSFw (VSFp### or VSFp###_YYYang, where YYY is collection angle). Also called beta. "
   VSFw, 1/m/sr," Filtered seawater volume scattering function plus VSF sal & temp contributions, i.e., VSFw = VSF - VSFp (VSFw### or VSFw###_YYYang, where YYY is collection angle). Also called beta., where YYY is collection angle). Also called beta., where YYY is collection angle). Also called beta. "
   water_depth, m, The water (bottom) depth where the data were collected 
   waveht, m, Wave height 
   wavelength, nm, Wavelength of measurement 
   wdir, degrees," Wind direction, described in degrees from north, increasing clockwise, increasing clockwise, increasing clockwise, increasing clockwise "
   wind, m/s, Wind speed 
   Wt, degreesC, Water temperature 
   Wvp, cm, Water vapor 
   year, yyyy, Sample year 
   Z_90, m, Depth of the first optical layer (37% light level) 
   Z_DCM, m, Depth of the deep chlorophyll maximum 
   Z_Eu, m, Depth of the euphotic layer 
   Z_MLD, m, Depth of the mixed layer 
   Zea, mg/m^3, HPLC Zeaxanthin 
```