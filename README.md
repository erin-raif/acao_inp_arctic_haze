# acao_inp_paper_fig_dev
A repository for the development of figures for the first paper. This contains all the code required to analyse the data and to obtain the figures in the paper.

## Requirements:
All python packages required are contained in requirements.txt.
Of note is faamasd, a python package developed for this paper which allows particle-size distributions to be obtained using FAAM data.
### Package breakages:
This deliberately uses xarray version 2022.6.0 and pandas 1.5.3 to avoid some changes to the underlying code that can cause this to break. If you are getting errors running anything, check these first. These were chosen because of bugs in the later versions which were yet to be fixed - the newest versions may avoid these, I have not checked. Functionality should not change.

## Data Sources:
Aircraft data can be found in the [CEDA archive](http://catalogue.ceda.ac.uk/uuid/ee96bac7c6e747c3b74ff952634ff2d7).

*Nevzorov cloud flags produced by Steve Abel use this aircraft data, though the code to produce these is not included in this archive. Please contact steven.abel "at" metoffice.gov.uk to obtain them.

Sea-ice files come from NOAA's [MASIE-NH (Multisensor Analyzed Sea Ice Extent - Northern Hemisphere) product](https://doi.org/10.7265/N5GT5K3K)

Many of the previous Northern Hemisphere measurements of INP recorded in Fig 4 were collated by [Porter, et al. 2022](https://doi.org/10.1029/2021JD036059). Southern Hemisphere measurements were collated by [Murray, et al. 2021](10.5194/acp-21-665-2021).

Satellite imagery comes from  NASA's [Global Imagery Browse Services (GIBS)](https://www.earthdata.nasa.gov/eosdis/science-system-description/eosdis-components/gibs), part of NASA's Earth Observing System Data and Information System (EOSDIS).

ERA5 reanalysis data is from the [Copernicus Climate Change Service](https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview).


## Figures
Each figure used in the paper has its own Jupyter notebook. These can be run without running the analysis code, all the data is dumped.

Figure 01 - Side-by-side plot of the flight tracks with satellite imagery. *Note that to reproduce this code with the satellite image, you may need to adjust source code of the OWSLib package due to a server-side change by NASA after the original creation for which OWSLib has not yet been updated to handle. Instructions on how to do this are contained in the appropriate Jupyter notebook. A ticket with this proposed fix has been raised in the appropriate python libraries, so hopefully this will be unnecessary in the newest versions of Python. Alternatively, simply comment out all the satellite image lines!*

Figure 02 - Locations of filter sampling.

Figure 03 - INP concentrations and normalisation by aerosol quantities.

Figure 04 - Other Arctic INP measurements. **Note: Code is included for completeness but data from other field campaigns is not packaged. This is available from repositories and authors.**

Figure 05 - Particle size distribtions for each filter leg

Figure 06 - Aerosol profiles

Figure 07 - SEM analysis

Figure 08 - Active site densities and comparison to other campaigns

Figure 09 - Variation of active site density and INP concentration with altitude 

Figure 10 - Relative INP concentrations in flight c280

Figure 11 - Backtrajectories.

Figure A1 - As Figure 3, but with each individual sample noted.

Figure A2 - As Figure 5, but with each individual sample noted.

Figure B1 - Functional form fitting (using output from functional_forms_v2).

## Analysis

These are jupyter notebooks that allow you to recreate the analysis.

calculate_INP_concentrations.ipynb - Calculate the INP concentrations and their errors.

generate_size_distributions.ipynb - Generate aerosol size distributions based on an assumed refractive index for the aerosol. Use these to normalise the INP concentrations by aerosol size, surface area and volume.

functional_forms_v2.ipynb - Uses a Latin hypercube method to find a best fit of a complex functional form to the data.