# Antarctic coastal blooms analysis code

**This repository contains the analysis code for Ha et al., "Intensification of Antarctic coastal phytoplankton blooms mediated by a lengthening ice-free season", submitted.**

Please contact me at [ethancc@uw.edu](mailto:ethancc@uw.edu) if you have any questions regarding this code, which was authored together with Rachel Ha.

## Attribution
If using the code and/or model data in an academic publication, we encourage you to provide the following citations, as appropriate:
* **Manuscript (pending)**: Ha, R.Y., Campbell, E.C., Young, J.N. (submitted). Intensification of Antarctic coastal phytoplankton blooms mediated by a lengthening ice-free season.
* **Code archive**: Campbell, E.C., Ha, R.Y. (2026, August 31). Analysis code for Ha et al. on Antarctic coastal blooms, v1.0.0. Zenodo. doi:[TBD](URL_TBD)

This code is freely available for reuse as described in the MIT license included in the repository.

## Description

This repository contains Python code and relevant files for running the analyses and generating the figures presented in the associated study. The input data sources are all publicly available, with the exception of the CDW residence time estimates from Tamsitt et al. (2021), which are archived in this repository (see "Data Availability Statement" in the paper).

## Prerequisites and instructions

1. Python 3 and `conda` (or `mamba`) should be installed. The [Anaconda](https://www.anaconda.com/download) distribution is recommended.

2. Clone or download this GitHub repository, which will provide a directory structure that includes the Tamsitt et al. data and ancillary files such as geospatial grids.

3. Recreate the required Python environment with all dependencies using the provided `coastal_blooms.yml` environment file. From within the repository, execute `conda env create -f coastal_blooms.yml` (you can also substitute `conda` with `mamba`, if preferred). This will create a new environment called `coastal_blooms`. Next, activate the environment using `conda activate coastal_blooms`.

4. Open and follow the two code notebooks, using `coastal_blooms_download_data.ipynb` first to download and process some key input data files. Second, use `coastal_blooms.ipynb`, the main notebook, to run the additional processing, analysis, and figure generation code.

- Start by running the **"Preamble"** notebook cells. Verify that the `conda` environment is functioning correctly.
- You will have to update the directory names as needed. Mainly, the variable `data_dir` should be updated to point to the location of the `Data/` directory within this repository on your system.
- The remaining sub-directory paths should be updated only if you wish to use pre-existing input data files downloaded on your system. However, this is not recommended, since this code processes and re-exports some input data files and thus expects them in a different format than how they were originally downloaded.
- The ERA5 download routine requires an ECMWF account as well as local installation of a Copernicus CDS API key; see [here](https://cds.climate.copernicus.eu/how-to-api) for how to set this up. If you see "Request is queued" after running the ERA5 download code, the request has been successfully submitted and you can exit using `Ctrl-C`. You can track the status of your ERA5 download requests and obtain the download links at [cds.climate.copernicus.eu/requests?tab=all](https://cds.climate.copernicus.eu/requests?tab=all), then use `wget` or similar to download the ERA5 files into `Datacd/ERA5/ERA5_original/`. Please see the documentation in the notebook for more info. Once the ERA5 data have been downloaded, use the final boolean switch (`process_era5`) to process the ERA5 data. You can delete the original files moved to `Data/ERA5/ERA5_original/To delete/` after this finishes.
- Note that most of the code operates using a series of boolean switches to avoid triggering unwanted modification of data files and variables.
