# Social Vulnerability Index Based on Data Extracted from HRSA's Uniform Data System
R code to extract, clean, and transform Uniform Data System for use in computing a social vulnerability index

# Background
Each year, Federally-Qualified Health Centers (FQHC's) are required to submit detailed reports containing aggregate data describing characteristics of the services they provide, workforce, and patient panels. This Uniform Data System (UDS) is a robust data source that can be used for population health projects.  An interesting population health project involves constructing a social vulnerability index (SVI) using specific variables dervied from UDS.

'The Center for Disease Control and Prevention (CDC) SVI uses 15 U.S. census variables to identify communities needing support before, during, or after disasters. It provides social vulnerability data at the state, county, and census tract levels across the U.S.' (CDC,2024)

# Purpose
The purpose of this repo is to share code that can be used to identify FQHC's of interest within a defined geographic region, extract select variables from source data, clean and prep this data for downstream use, compute the SVI, and visualize results.  Sharing this code may help researchers understand the relative risk of social needs and health disparities among patients in the panel of target health centers.

# Processing Steps
* Step 1: Environment Setup - Call packages needed for data prep and analysis
* Step 2: Select FQHC's of interest - Identifies all zip codes within a defined set of states and counties, then uses this dataset to filter UDS data to target centers in those zip codes.
* Step 3: Process the UDS data - Requires a user-created Excel workbook that identfies variables of interest within the UDS data for the centers identified in Step 1. This code reads in each dataset from the UDS source workbook and filters to the specified variables. The code writes the output data to the working directory.
* Step 4: Clean and prepare the data for analysis - Reads in the data generated during Step 3 and performs data quality checks. Recodes missing data points. Consolidates datapoints into variables defined in the map. Computes raw rates associated with each variable. Checks the variability within each datapoint to ensure all variables should be kept. The code writes the output data to the working directory.
* Step 5: Compute the SVI and analyze results - Reads in the data generated during Step 4 and applies the methods described by the CDC to compute SVI at the variable, theme, and overall levels.  The code generates some visualizations to facilitate understanding of results.

# Included Files
* h80-2023.xlsx and lal-2023.xlsx are UDS data files downloaded from the HRSA site; these were used to develop the methodology. You may download more updated files.
* factor_map.xlsx is the workbook that you need to create which maps your desired Themes and Variables to the UDS data.
* total_patient_mapping.png is a screenshot of the this tab required in the factor_map.xlsx workbook to show structure and content; it is included to display in the markdown output.
* index_mapping.png is a screenshot of this tab required in the factor_map.xlsx workbook to show structure and content; it is included to display in the markdown output.
* uds_svi_process.Rmd is the markdown file that runs all of the code and displays the output in a notebook-style format.

# Project Directory Structure
uds_svi/

|- h80-2023.xlsx
|- lal-2023.xlsx
|- factor_map.xlsx
|- total_patient_mapping.png
|- index_mapping.png
|- uds_svi_process.Rmd

# References
1. Health Resources & Service Administration. (2025). Uniform Data System files for download https://www.hrsa.gov/foia/electronic-reading
2. Centers Disease Control and Prevention (CDC)/ Agency for Toxic Substances and Disease Registry (ATSDR). (2024).
   * Social Vulnerability Index overview https://www.atsdr.cdc.gov/place-health/php/svi/
   * SVI Methodology Documentation https://svi.cdc.gov/map25/data/docs/SVI2020Documentation_08.05.22.pdf
