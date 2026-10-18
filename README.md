# UCAR/CU CYGNSS v3.2 Data Analysis in Google Earth Engine

## Overview
This repository contains a collection of Jupyter notebooks for visualizing, analyzing, and comparing CYGNSS data with other geospatial datasets available through Google Earth Engine (GEE).
The notebooks are designed to support the exploration of CYGNSS observations, the analysis of their spatial and temporal patterns, and comparisons with complementary Earth observation or environmental datasets.
The repository provides a reproducible workflow for accessing geospatial data, generating visualizations, and conducting comparative analyses using Python and Google Earth Engine.

## Objectives
This project will help you to start wotk with CYGNSS data in GEE environment. The main objectives of this project are to:

- Visualize CYGNSS data and explore its spatial distribution.
- Analyze the spatial and temporal characteristics of CYGNSS observations.
- Compare CYGNSS data with selected datasets available in Google Earth Engine.
- Generate maps, plots, and summary statistics to support data interpretation.
- Provide reusable Jupyter notebooks for geospatial analysis and research.

## Data Sources

# CYGNSS
The UCAR/CU CYGNSS v3.2 inundation maps provide estimates of fractional surface water extent derived from NASA’s Cyclone Global Navigation Satellite System (CYGNSS). The temporal range of UCAR/CU CYGNSS v3.2 data is 1 August 2018 to 31 December 2025, and each corresponding daily file contains five distinct variables: 

- 1-day inundation observations, containing retrievals for valid, directly observed grid cells (no spatio-temporal inter-polation);
- 3-day interpolated inundation, obtained by interpolating three-day observation aggregates;
- interpolation flags, distinguishing directly observed and interpolated grid cells in the three-day product;
- 1-day inundation anomalies, expressing departures of daily observations from the seasonal cycle;
- 3-day interpolated inundation anomalies ex pressing departures of the three-day interpolated values from the seasonal cycle.

The dataset has a spatial resolution of 3 km and geographic coverage extending approximately from 38° N to 38° S, consistent with the CYGNSS orbital inclination.

UCAR/CU CYGNSS v3.2 dataset is available in GEE as an collection of imagesunder name "projects/sat-io/open-datasets/CYGNSS/inundation"

# GEE datasets used in the project
This project uses couple of geospatial datasets available at GEE. These are:

- satellite imagery: Sentinel-2 Level-2A used to generate cloud-masked median composites (10 m spatial resolution for RGB bands; COPERNICUS/S2_SR_HARMONIZED)
- precipitation: GPM IMERG satellite-based precipitation estimates provided every 30 minutes, with approximately 11 km spatial resolution (NASA/GPM_L3/IMERG_V07)
- enhanced vegetation index: MODIS Terra vegetation indices (EVI) provided as 16-day composites at 250 m spatial resolution (MODIS/061/MOD13Q1)
- land cover: ESA WorldCover global land cover map for 2021, distinguishing 11 land cover classes at 10 m spatial resolution (ESA/WorldCover/v200)
- population density: WorldPop gridded population data providing estimates of the number of people per grid cell at approximately 100 m spatial resolution (WorldPop/GP/100m/pop)

## Requirements

The notebooks use Python and Google Earth Engine. 
1. It is necessarry to install earthengine.api and create an account with aproject at Google Earth Engine. 
2. To properly run the notebooks it is necesarry to create an environment with:
- ee
- geemap
- cmocean
- matplotlib
- numpy
- colormaps

All dependencies and requirements are listed in requirements.txt.
## Installation and Setup

1. Clone or download this repository.
2. Create and activate a Python environment.
3. Install the required dependencies:
    pip install -r requirements.txt
4. In each notebook replace 'project_name'  with your Google Cloud project ID configured for Earth Engine.
5. Open the notebooks in JupyterLab or another compatible Jupyter environment.

## Notebooks and Usage

### 1. CYGNSS Visualization

File: notebooks/simple_plot_CYGNSS.ipynb

Purpose:

Display CYGNSS data on interactive maps.

## Important Considerations
While further working with CYGNSS data in GEE please note that  all bands in 'projects/sat-io/open-datasets/CYGNSS/inundation' collection are encoded as 8-bit integers representing values between 0 and 255. The valid range for fractional inundation values (for both 1-day observations and 3-day inundation maps) is 0–100, encoded as a percentage of the grid-cell area. To get actual fractions, one needs to divide this value by 100. The valid range of anomaly bands (both 1-day inundation anomalies and 3-day interpolated inundation anomalies) is 0–200. For an encoded value x, the anomaly fraction is (x − 100)/100. The resulting anomaly fractions range
from −1 to 1. Pixels with no valid data are assigned a value of 255.

This preprocessing procedure is implemented by the 'mask_inundation(image)' and 'mask_anomalies(image)' definitions, in each of the notebooks.

## Citation
If you use this repository in research, please cite the repository and the original CYGNSS and comparison-dataset publications.

Repository citation: [Add the preferred citation, DOI, or repository URL.]
Paper citation: 

## Contact

For questions or suggestions, please ...




