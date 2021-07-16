# Pre-Registration of Rpr - Reproduction of Kang et al 2020 Rapidly measuring spatial accessibility of COVID-19 healthcare resources: a case study of Illinois, USA

Joseph Holler, Department of Geography, Middlebury College, Middlebury VT 05753 <br>
Kufre Udoh, Department of Geography, Middlebury College, Middlebury VT 05753 <br>
Derrick Burt, Department of Geography, Middlebury College, Middlebury VT 05753 <br>
Drew An-Pham, Department of Geography, Middlebury College, Middlebury VT 05753 <br>
Students of GEOG 0323, Department of Geography, Middlebury College, Middlebury VT 05753 <br>

Version 1.0 | Created June 30, 2021 | Last Updated July 1, 2021 <br>

## Abstract

Kang, Michels, Lyu, Wang, Agbodo, Freeman and Wang ([2020](https://doi.org/10.1186/s12942-020-00229-x)) published a report outlining a quick and reproducible methodogy that measures and visualizes the access that two different populations, COVID-19 patients and the population risk (defined as those over 50), have to two important resources, ICU beds and Ventilators. To rapidly measure accessibility to Covid-19 healthcare resources, Kang et al. developed a methodology for [parallel implementation](https://www.omnisci.com/technical-glossary/parallel-computing#:~:text=Parallel%20computing%20refers%20to%20the,part%20of%20an%20overall%20algorithm.) of an Enhanced Two-Step Floating Catchment Area (E2FSCA) methodology. This method calculates the ratio between a service feature (in this scenario, hospital ICU beds or ventilators) and the population in its surrounding area, accounting for distance decay. Because this is a computationally intensive analysis that uses large street networks, the authors developed a parallel-E2FSCA (P-E2FSCA), which enables the simultaneous use of up to 4 processors while implementing the analysis.

This reproduction study is motivated by three factors. First, measuring the accessibility of COVID-19 healthcare resources may allow for a more accurate allocation of healthcare resources. Second, a fully reproducible publication can be more readily replicated in new geographic, temporal, and thematic contexts, and tested for uncertainty due to data constraints and subjective modeling decisions. Third, the CyberGISX platform is a new technology capable of making geographic research both more computationally efficient, interoperable, and accessible; establishing standards for conducting reproducible research in this context is a vital step towards realizing the potential benefits of CyberGIS.

In this study, we attempt to identically reproduce the 2020 spatial accessibility measurements of Covid-19 healthcare resources for the city of Chicago using the Python Jupyter Notebooks in the University of Illinois Urbana-Champaign CyberGISX platform. We do not attempt to reproduce the 2020 spatial accessibility measurements of Covid-19 healthcare resources for the entire state of Chicago, nor do we attempt to reproduce the social vulnerability characteristic results of high and low accessibility areas. We will compare our reproduction results with the original results using a Spearman's Rho Correlation Coefficient.

The replication study data and code will be made available in a GitHub repository to the greatest extent that licensing and file sizes permit. The reproduction will be performed entirely using the [CyberGISX platform](https://cybergisxhub.cigi.illinois.edu/) with Python (3.7.6) Jupyter Notebooks. The package specifications are outlined in the repository's procedure folder. The repository will be made public at [github.com/GIS4DEV/RP-Kang](https://github.com/GIS4DEV/RP-Kang).

Kang et al. 2020. Rapidly Measuring Spatial Accessibility of COVID-19 Healthcare Resources: A Case Study of Illinois, USA. *International Journal of Health Geographics* 19:36. DOI:[https://doi.org/10.1186/s12942-020-00229-x](https://doi.org/10.1186/s12942-020-00229-x).

### Keywords

CyberGIS, COVID-19, Social vulnerability, Spatial accessibility, Reproducibility, Healthcare resources

## Study design

The reproduction study design will try to implement the original study as closely as possible to reproduce the spatial accessibility measurement for Chicago (F7) and the distribution of the accessibility measure (F8). Our two confirmatory hypotheses are that we will be able to independently reproduce results for all four maps and all four histograms.

The working hypothesis are:

> H1: There is no correlation between Kang et al's spatial accessibility measurement of healthcare resources in Chicago and our reproduction study's spatial accessibility measurement of healthcare resources in Chicago.

> H2: There is no correlation between Kang et al's distribution of accessibility measurement of healthcare resources in Chicago and our reproduction study's distribution of accessibility of healthcare resources in Chicago.


### Original study design


The original study is **observational** and **descriptive**, with no hypotheses or effect sizes.

The study measures the spatial accessibility of a single healthcare resource (ICU beds or ventilators) to a single population (At-risk or Covid-19 patients).

The **spatial extents** of the study were the state of Illinois and the city of Chicago (separate analyses). We will only reproduce the results for Chicago.
The **spatial scales** of the analysis were variable dependent. The at-risk population data were measured at the census tract level geography . The Covid-19 cases were measured at the zip code level geography. The final results were reaggregated in 500-meter hexagonal grids.
The **temporal extent** of the study was also variable dependent. The Covid-19 was a cumulative case count from the beginning of collection (~late Feb 2020-Apr 10,2020). The ACS population and geographic data was collected in 2018.

There is no **randomization** in the original study.

The spatial interaction measurement, distances, and  weighting schemes were selected primarily based on pre-existing criteria for measuring spatial accessibility of resources to a defined population.
The authors contextualized these methods within healthcare geography literature. They select a enhanced two-step floating catchment area (E2SFCA), citing it as a "commonly used method for measuring spatial accessibility."  
The author's do not offer a justification for their use of distance or weighting schemes but they do imply on page 2 that the the 10, 20, and 30 minute travel times are pre-set distance of thee E2FSCA method.

The study was originally conducted in CyberGIS Jupyter Notebooks using Python (3.7.6). The original study materials can be found at [https://github.com/cybergis/COVID-19AccessibilityNotebook](https://github.com/cybergis/COVID-19AccessibilityNotebook). It should be noted that this repository does not cover the paper's entire methodology.


## Sampling Plan

### Existing data and data exploration

This registration is based upon knowledge of the original study based upon a thorough reading to the original research article and a thorough understanding of the data.

In full transparency, we have already attempted the reproduction study, including acquisition and analysis of all of the secondary data sources required.
This preregistration serves two purposes for us:
1. Revisiting the original paper to document the most complete knowledge of the data and methodology possible without acquiring data or beginning analysis, represented in this preregistration.
1. Practicing and demonstrating the full workflow of a reproduction study in the human-environment and geographical sciences, including preregistration, reproducible computational research practices, and publication of a reproduction report.

### Data collection and spatial sampling

The study exclusively uses secondary data sources. To avoid confusion, the following section will only refer to the data used for the Chicago analyses as this reproduction does not attempt to reproduce the results from the state of Illinois.

The published results are based on Covid-19 cases reported at the zip code level. Because this varies state-to-state, researchers do not have full control over the spatial scale of the sampling.

**A BIT CONFUSED ABOUT SPATIAL SAMPLING HERE**


## Data description

All of the raw data necessary for our specific reproduction is provided by the authors in their Github repository,[github.com/cybergis/COVID-19AccessibilityNotebook](https://github.com/cybergis/COVID-19AccessibilityNotebook). The authors do not, provide the Illinois Street Network, as it is too large for GitHub, nor do they provide the Census SVI data, presumably because they do not include this portion of this analysis in their notebook.

Covid-19 case data is derived from Illinois Department of Public Health (IDPH). Data was collected from the beginning of the pandemic (late February 2020) to April 10, 2020 and provides a cumulative case count. The website, [www.dph.illinois.gov/covid19/covid19-statistics](https://www.dph.illinois.gov/covid19/covid19-statistics), is provided in the original report but has been modified as the original link returns a 404 error. This link does not appear to provide access to archived datasets, so only the most recent case counts can be downloaded from the website.

Hospital data was acquired from the U.S. Homeland Infrastructure Foundation Level Data (HIFLD). The website, [www.hifld-geoplatform.opendata.arcgis.com/datasets/geoplatform::hospitals/explore](https://hifld-geoplatform.opendata.arcgis.com/datasets/geoplatform::hospitals/explore) is not provided in the original paper, but can be accessed from the provided link. The authors filter out "military, children, psychiatric, and rehabilitation" hospitals in the study, resulting in a total of 66 hospitals for Chicago.

The Covid-19 case data were joined to zip code geographies; the authors do not specify the source of the zip code geographies in the paper but based on examination it is evident that they were derived from the U.S. Census Bureau. The authors do not provide summary statistics in the paper but the provided dataset yields 86 zip codes for Chicago. The authors do not provide a link for the original dataset but the ACS 2018 5-yr zip level data can be found at this website, [www.data.census.gov/cedsci/advanced?t=Age%20and%20Sex&y=2018&d=ACS%205-Year%20Estimates%20Detailed%20Tables](https://data.census.gov/cedsci/advanced?t=Age%20and%20Sex&y=2018&d=ACS%205-Year%20Estimates%20Detailed%20Tables). Zip code shapefiles can be downloaded from this website, [www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html), or by using the census ftp, available here, [ftp2.census.gov]( ftp2.census.gov.).

Population data for the At-risk population variable were pulled from the Census 2018 ACS 5-year estimates using a census API key. These data were joined to census tract geographies. Again, the authors do not specify the source of the tract geographies in the paper but based on examination it is evident that they were derived from the U.S. Census Bureau. The authors do not provide summary statistics in the paper but the provided dataset yields 878 zip codes for Chicago.
The authors do not provide a link for the original dataset but the ACS 2018 5-yr tract level data can be found at the census website, [www.data.census.gov](https://data.census.gov/cedsci/table?t=Age%20and%20Sex&y=2018&d=ACS%205-Year%20Estimates%20Detailed%20Tables&tid=ACSDT5Y2018.B01001&hidePreview=true), or automatically downloaded using the python package, [CensusData](https://pypi.org/project/CensusData/). Tract shapefiles can be downloaded from this website, [www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html), or by using the census ftp, available here, [ftp2.census.gov]( ftp2.census.gov.).

Street network data was provided by OSMNX, a python package that combines OSM data with network analysis algorithms from the python package, NetworkX. The authors pull a street network for both Illinois and Chicago. They do not indicate the exact date that they pulled the network, but provide a copy of the Chicago Network in their notebook. This is important because the street network is regularly updated and changed and reproducing the results exactly requires using the same street network. Full documentation the python package can be found at [github.com/gboeing/osmnx](https://github.com/gboeing/osmnx).

## Variables

All variables used in this study are derived from secondary data.

**Do the distance weights count as *experimentally manipulated* variables?**

**In general, a bit confused about the framing of variables in this study**


#### Attribute variable transformations


#### Geographic transformations

Both tract-level and zip-code level data for at-risk and covid-case populations are provided in their original administrative geographic scale. They are transformed into centroids and joined to any intersecting catchment areas.

The catchment areas (with the joined population + covid data) are then re-aggregated into 5-km hexagonal grids by intersecting the catchments and the hexagons and dividing the. The author's use hexagonal grids to "minimize orientation bias from edge effects."

## Analyses

The final spatial accessibility of healthcare resources is a normalized score (scale of 0 to 1, calculated for each hexagon with the following eq: ```normAcc(i) = (Acc(i) - min(Acc))/(max(Acc) - min(Acc))```). This normalized score is calculated four times in total, covering each permutation of the two healthcare resources (ICU beds and hospital vents) to the two populations (at risk and Covid patients). In the paper, the authors provide the results on a map using a classified color scheme. They also provide a histogram of the distribution and the location of the mean. In the notebook, they only provide code to produce the output maps with a continuous scheme.

### Geographical characteristics

The **coordinate reference system(s)** used in the original study are not specified. While the analysis uses distance as a criteria, it is likely measured in drive time using the OSMNX package, and therefore, as long as the coordinate reference system is consistent across all layers, (re)projection should not be necessary and only considered for cartographic purposes.

The **spatial extents** of the study were both the state of Illinois and the City of Chicago (presumably the census' place defined boundaries). For  our reproduction, we will only perform the analysis on the city of Chicago (OSM relation [122604](https://www.openstreetmap.org/relation/122604#map=10/41.8343/-87.7327)) excluding unpopulated tracts or zip code geographies with 0 covid cases.

**Edge effects** are partially addressed in this analysis. When aggregating the results into accessibility grids, the authors choose to use hexagonal grids to account for directional bias of edge effects. However, when establishing their accessibility criteria scores for both Illinois and Chicago, the authors do not account for the possibility of populations that live outside the state or city seeking care within these regions.

The authors provide a framework to conduct this analysis across **multiple spatial scales**. This is evident in the use of different administrative geographies and a modifiable hexagonal output grid.  

The **spatial support** for the final analysis of spatial accessibility is a 5-km hexagonal grid. The authors explain their reasoning behind this decision: "In Chicago, 400 meters are the shortest distance between zip code centroids. Therefore, 500-meter hexagon grids are sufficient to represent the accessibility measure.

The analysis does not include creation of any **spatial subgroups** and does not measure or account for any **first order spatial effects**, **second order spatial effects**, or **spatial anistropies**.


### Temporal characteristics

The **temporal extent** of the original study is dependent on the population and resource input variables. The COVID-19 cases represent cumulative count of covid cases "as of April 10, 2020," but the authors do not indicate the date at which the IDPH started recording cases. The at risk population are 5 year estimates of tract populations from 2014 to 2018. The temporal extent for the hospital ventilators and ICU beds is not made explicit in the paper, but the online dataset provides a validation date for each features.

**Unsure about temporal support**.

**Temporal effects** are not measured or accounted for

### Data exclusion

Most of the data provided in the original study's Github repository has already been pre-processed to deal with missing data.
The streeet network for Chicago has a large portion of **missing data**, specifically the street speed limits. The authors make an **inference** that the average speed limit is 35mph for these missing values. This is not mentioned in the paper but can be identified in ```network_setting``` function that cleans the street network.

The study does not analyze the presence of **outliers** or exclude them.
The study does not **weight samples**.

### Analytical specification

There are no hypothesis tests requiring explanation of analytical specifications.

### Inference criteria and robustness

There are no hypothesis tests requiring explanation of inference criteria or robustness.

### Exploratory analyses and contingency planning

The entire study is an **exploratory analysis** in using a parallel computing method to implement a P-E2SFCA to measure spatial accessibility of healthcare resources.
The authors do not outline any **contingency plans**.

## Reproduction study design

This reproduction study will focus on reproducing spatial accessibility results for Chicago (F7 & F8), excluding the spatial accessibility analysis for Illinois and the portion that incorporates SVI data.
The aim of this reproduction is to produce results identical to the original study.
The reproduction will use the indicators and weights as they are described in the original study.
The reproduction study will use the same software environment, using Python (3.7.6) Jupyter Notebooks in the CybgerGISX environment.
The research will be completed in full by accessing the CyberGISX environment from both Windows 10 and MacOS operating systems. Given the parallel computing processes, running these notebooks in a cyberinfrastucture environment is recommended.
Here is a complete list of required Python modules:

* pandas==1.0.3
* numpy==1.18.1
* geopandas==0.7.0
* networkx==2.4
* osmnx==0.11.4
* shapely==1.7.0
* matplotlib==3.1.3
* tqdm==4.45.0
* folium==0.10.1

### Planned differences from the original study


The study will atteept to reproduce the original methods exactly, but some deviations will be inevitable due to ambiguous information in the original article.
1. The road network used in the original analysis (or, at least in the provideed notebook) was restricted to the bounds of Chicago. Thus, the original notebook does not includee hospitals outside the city limits and creates a boundary effect that inaccurately portrays accessibility for Chicago. To fix this, we included a 15-mi (24km) buffer that accounts for a 30-minute drive time outside of the city (at 30mph)
2. Adding this buffer introduces errors in the OSM syntax. Namely, string characters in the 'maxspeed' column. The following code allows us to remove thos characters:
**I'm not sure if this counts as a planned deviation**
3. We will add code to benchmark processing time on important sections of code. 
4. We plan to add code to produce the same classifide output maps provided in the results of the original study. 

In addition to this, we have compiled two separate notebooks. In one, we deviate from reproducing the exact results and instead aim to add improvements to the original code that we deem more appropriate for the given analysis. In the other, we compile code to automate the pre-processing steps that the original notebook fails to include. We believe this will facilitate a more reproducible and replicable methodology.

In the improvements notebook, we intend to:
1. Add code to summarizee the road network avg speeeds before and after the ```network_setting``` function is run.
2. Improvee the ```calculate_catchment_area``` function to avoid calling computationally intensive functions multiple time. Instead of using spatial algorithms like ```nx.ego_graph```, we will use ```nx.single_source_dijkstra_path_length``` to create a dictionary of nodes, and query those nodes to create 10, 20, and 30 minute drive-time polygons. This function will be called ```dijkstra_cca_polygons```
3. We will add options to run the code with different weighting schemes. Kang et al (2020) applied a set of weights (1.00, 0.68, & 0.22) to respective travel time zones (0-10, 10-20, & 20-30 min) to account for distance decay in their analysis. Though not explained in their methodology, these weights were likely derived from Luo & Qi's (2009) paper, which used the same E2SFCA method to assess spatial accessibility to primary care physicians in northern Illinois. In their results, Luo & Qi (2009) referenced a second weight set that represented a shaper distance decay: 1.00, 0.42, & 0.09. Another weighting scheme can be found in 
Delamater, Shortridge, and Kilcoyne (2019). They derive a logistic cumulative distance function, with distance decay based on distance to the nearest facility for a population, and find this to be the most accurate weight values for healthcare service distance decay: 1.0, 0.5, 0.1. Both thesee weighting schemes are provided in the improvements code.

In the pre-processing notebook, we intend to automate pre-processing steps for:
- Covid-19 Cases (and corresponding zip code shapefiles)
- Tract population data (and corresponding tract shapefiles)
- Hospital data
- Chicago hexagon grid

### Evaluating the reproduction results

In order to evaluate the reproduction results, we will 


## Referencing the original paper

Kang et al. 2020. Rapidly Measuring Spatial Accessibility of COVID-19 Healthcare Resources: A Case Study of Illinois, USA. *International Journal of Health Geographics* 19:36. DOI:[https://doi.org/10.1186/s12942-020-00229-x](https://doi.org/10.1186/s12942-020-00229-x).


### Sections

1. Introduction
2. Data and method
  - Study area and data
  - Parallel enhanced two-step floating catchment areas (P-E2SFCA) method
3. Results
  - Socioeconomic and demographic characteristics in high and low accessibility
  - Computational performance
4. Concluding Discussion 


### Tables, figures, other elements

- F1 Datasets of hospital population, COVID-19 cases in Illinois
- F2 Datasets of hospitals, population, COVID‐19 cases in Chicago, Illinois
- F3 Measure spatial accessibility of a set of hospitals
- F4 E2SFCA algorithm
- F5 Computational workflows
- F6 Expression of accessibility measures on hexagon grids
- F7 Spatial accessibility measure in Chicago
- F8 Accessibility measure in Chicago
- F9 Accessibility measure in Illinois
- F10 Accessibility measure in Illinois
- F11 Acceessibility measure
- F12 Comparison of spatial accessibility measure
- F13 Social vulnerability characteristics in high and low accessibility areas based on the spatial accessibility measure for population at risk

## Other references

Luo, W., & Qi, Y. (2009). An enhanced two-step floating catchment area (E2SFCA) method for measuring spatial accessibility to primary care physicians. *Health & place*, 15(4), 1100-1107.

Delamater, P.L., A.M. Shortridge, and R.C. Kilcoyne. 2019. Using floating catchment are (FCA) metrics to predict health care utilization patterns. BMC Health Services Research 19:144. https://doi.org/10.1186/s12913-019-3969-5.
