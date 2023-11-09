# Project Part 1: Common Analysis of Fires

This repository contains the data files, code and results of Project Part 1, for the course Data 512: Human Centered Data Science at the University of Washington's MS in Data Science program.

## Goal of Project
In recent years, the western United States has been experiencing increasingly severe wildfires, resulting in widespread smoke that affects multiple states. While the causes of these wildfires are debated, including factors like climate change and forestry policies, their impact is undeniable. 

This project focuses on assessing how wildfires impact Gillette, Wyoming, with the ultimate objective of providing valuable insights to policymakers, city administrators, and local authorities. By understanding these impacts, they can make informed decisions on how to prepare for and mitigate the consequences of future wildfires.

## Goal of Assignment

The goal of this assignment is to answer the following research question: 

_What are the estimated smoke impacts on Gillette, Wyoming for the last 60 years?_

This assignment creates an estimate of wildfire smoke. This estimate is a number that will eventually be used to build a predictive model. Technically, smoke impact should probably be considered the health, tourism, economic or other social problems that result from the smoke. The smoke estimates adheres to the following conditions:

* The estimate only considers the last 60 years of wildland fires (1963-2023).
* The estimate only considers fires that are within 1250 miles of your assigned city.
* An annual fire season will run from May 1st through October 31st.

## Resources Used
- Editor used: VS Code
- Python version: 3.9.18
- Packages used: json, time, pyproj, geojson, tqdm, pandas, requests, datetime, collections, seaborn, 
matplotlib, numpy, statsmodels.

## API Documentation
- [Pyproj](https://pyproj4.github.io/pyproj/stable/index.html)
- [geojson](https://pypi.org/project/geojson/)
- [Air Quality System API](https://aqs.epa.gov/aqsweb/documents/data_api.html)

## Project Organization

This project has the following structure:
```
.
├── results/
│   ├── Mehjabeen Zameer - DATA 512 Project Part 1
├── code/
│   ├── Analysis of Wildfires.ipynb
├── LICENSE
└── README.md
```
## Steps to Reproduce This Research

1. Install the required resources as listed in the Resources header above. 
2. Run the Analysis of Wildfires.ipynb file.
3. Analyze results.

## Data 

Source Files:
- [Wildfire dataset](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81) This dataset was collected and aggregated by the US Geological Survey.  
- [FIPS](https://www.census.gov/library/reference/code-lists/ansi.html) The Federal Information Processing Standard Publication (FIPS) is a five-digit Federal Information Processing Standards code which uniquely identified counties and county equivalents in the United States, certain U.S. possessions, and certain freely associated states.
- [Sample Notebook for Calculating Geo Distances](https://drive.google.com/file/d/1qNI6hji8CvDeBsnLDAhJXvaqf2gcg8UV/view?usp=drive_link). This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - August 14, 2023
- [Sample Notebook for Extracting Air Quality Data](https://drive.google.com/file/d/1bxl9qrb_52RocKNGfbZ5znHVqFDMkUzf/view?usp=drive_link). This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - August 14, 2023

Intermediary Files:

- fire_data.csv: Wildfire incidents that occured between 1963-2023 that were less than 1250 miles from Gillette, Wyoming.  

The data files for the assigment were large in size (over 3 GB and 700 mb) and therefore not uploaded. However, these can be extracted using the links above and from the [code notebook](https://github.com/MehjabeenZ/data-512-project/blob/main/code/Analysis%20of%20Wildfires.ipynb). 

The table below describes some relevant data fields in the fire_data.csv file:

|Column|Description|
|---|---|
|`OBJECTID`|Unique identification for the table row|
|`USGS_Assigned_ID`|A unique ID assigned by the USGS creators of the dataset to the focal fire.|
|`Assigned_Fire_Type`|Assigned in the following order of dominance: Wildfire, Likely Wildfire, Unknown - Likely Wildfire, Prescribed Fire, Unknown - Likely Prescribed Fire|
|`Fire_Year`|The calendar year when the dataset creators determined the fire occurred.|
|`GIS_Acres`|The GIS calculated acres of the fire polygon calculated by using the Calculate Geometry tool in ArcGIS Pro.|
|`Distance`|Shortest distance in miles of the perimeter of the fire to Gillette.|

## Special Considerations
- Step 1.6 in the notebook takes a few hours to run. In the json file, some rings are labelled as 'curverings' which may interrupt the block of code. As these records are less than 50 in a file with over 135,000 records, these have been excluded in this analysis but may be considered by anyone looking to reproduce this research. 
- The United States Environmental Protection Agency (US EPA) was created in 1973 and began installing air quality monitoring stations in the 1980s. Further, of 3000+ counties in the US, the EPA has vetted monitoring stations in only 2000 of them. Therefore, there are quite a few null values when trying to extract and use the AQI data.

