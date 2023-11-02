# Pre-Registration of Rpr - Reproduction of Kang et al 2020 Rapidly measuring spatial accessibility of COVID-19 healthcare resources: a case study of Illinois, USA

Joseph Holler, Department of Geography, Middlebury College, Middlebury VT 05753   
Derrick Burt, Department of Geography, Middlebury College, Middlebury VT 05753
Kufre Udoh, Department of Geography, Middlebury College, Middlebury VT 05753   
Drew An-Pham, Department of Geography, Middlebury College, Middlebury VT 05753  
Students of GEOG 0323, Department of Geography, Middlebury College, Middlebury VT 05753  

Version 1.1 | Created June 30, 2021 | Last Updated February 24, 2023

## Abstract

Kang, Michels, Lyu, Wang, Agbodo, Freeman and Wang ([2020](https://doi.org/10.1186/s12942-020-00229-x)) published a report outlining a quick and reproducible methodology to measure and visualize the access that two different populations, COVID-19 patients and the population risk (defined as those over 50), have to two important resources, ICU beds and Ventilators.
To rapidly measure accessibility to Covid-19 healthcare resources, Kang et al. developed a methodology for [parallel implementation](https://www.omnisci.com/technical-glossary/parallel-computing#:~:text=Parallel%20computing%20refers%20to%20the,part%20of%20an%20overall%20algorithm.) of an Enhanced Two-Step Floating Catchment Area (E2FSCA) methodology.
This method calculates the ratio between a service feature (in this scenario, hospital ICU beds or ventilators) and the population in its surrounding area, accounting for distance decay.
Because this is a computationally intensive analysis that uses large street networks, the authors developed a parallel-E2FSCA (P-E2FSCA), which enables the simultaneous use of up to 4 processors while implementing the analysis.

This reproduction study is motivated by four factors.
First, measuring the accessibility of COVID-19 healthcare resources may allow for a more accurate allocation of healthcare resources, and to that end this this particular this study is the foundation for to a public dashboard, [Where COVID-19](https://wherecovid19.cigi.illinois.edu/).
Second, a fully reproducible publication can be more readily replicated in new geographic, temporal, and thematic contexts, and tested for uncertainty due to data constraints and subjective modeling decisions.
Third, the CyberGISX platform is a new technology capable of making geographic research both more computationally efficient, interoperable, and accessible.
Establishing standards for conducting reproducible research in this context is a vital step towards realizing the potential benefits of CyberGIS.
Fourth, the study is being used to teach methods of network analysis and health care accessibility analysis in a cyberinfrastructure environment to geography students.

In this study, we attempt to identically reproduce the 2020 spatial accessibility measurements of COVID-19 healthcare resources for the city of Chicago using the Python Jupyter Notebooks in the University of Illinois Urbana-Champaign CyberGISX platform.
We do not attempt to reproduce the 2020 spatial accessibility measurements of COVID-19 healthcare resources for the entire state of Illinois, nor do we attempt to reproduce the social vulnerability characteristic results of high and low accessibility areas.
We will compare our reproduction results with the original results using a Spearman's Rho Correlation Coefficient.

The replication study data and code will be made available in a GitHub repository to the greatest extent that licensing and file sizes permit.
The reproduction will be performed entirely using the [CyberGISX platform](https://cybergisxhub.cigi.illinois.edu/) with Python (3.7.6) Jupyter Notebooks.
The package specifications are outlined in the repository's procedure folder.
The repository will be made public at [github.com/HEGSRR/RPr-Kang-2020](https://github.com/HEGSRR/RPr-Kang-2020).

Kang et al. 2020. Rapidly Measuring Spatial Accessibility of COVID-19 Healthcare Resources: A Case Study of Illinois, USA. *International Journal of Health Geographics* 19:36. DOI:[10.1186/s12942-020-00229-x](https://doi.org/10.1186/s12942-020-00229-x).

### Keywords

CyberGIS, COVID-19, Social vulnerability, Spatial accessibility, Reproducibility, Healthcare resources

## Study design

The reproduction study design will try to implement the original study as closely as possible to reproduce the spatial accessibility measurement for Chicago (F7) and the statistical distribution of the accessibility measure (F8). Our two confirmatory hypotheses are that we will be able to independently reproduce results for all four maps and all four histograms.

The working hypothesis is:

> H1: There is no correlation between Kang et al's spatial accessibility measurement of healthcare resources in Chicago and our reproduction study's spatial accessibility measurement of healthcare resources in Chicago.

### Original study design

The original study is **observational** and **descriptive**, with no hypotheses or effect sizes.

The study measures spatial accessibility to health care resources in four unique combinations:
- Resource: ICU Beds and Population: COVID-19 cases
- Resource: ICU Beds and Population: People over age 50
- Resource: Ventilators and Population: COVID-19 cases
- Resource: Ventilators and Population: People over age 50

The **spatial extents** of the study were the state of Illinois and the city of Chicago (separate analyses). We will only reproduce the results for Chicago because of the prohibitive size and download time for a street network for the full extent of Illinois.
The **spatial scale** of the analysis is a 500-meter hexagonal grid.
The **temporal extent** of the study was also variable-dependent. The Covid-19 was a cumulative case count from the beginning of collection (~late Feb 2020-Apr 10,2020). The ACS population and geographic data was a five-year estimate ending in 2018.

There is no **randomization** in the original study.

The analysis follows the enhanced two-step floating catchment area (E2SFCA) method from health geography literature, implemented with parallel processing.

The study was originally conducted in CyberGIS Jupyter Notebooks using Python (3.7.6). The original study materials can be found at [https://github.com/cybergis/COVID-19AccessibilityNotebook](https://github.com/cybergis/COVID-19AccessibilityNotebook). It should be noted that this repository does not cover the paper's entire methodology.

## Sampling Plan

### Existing data and data exploration

This registration is based upon knowledge of the original study based upon a thorough reading of the original research article and associated Git compendium of data and code.

In full transparency, we have already attempted the reproduction study, including acquisition and analysis of all of the secondary data sources required.
This pre-registration serves two purposes for us:
1. Revisiting the original paper to document the most complete knowledge of the data and methodology possible without acquiring data or beginning analysis, represented in this preregistration.
1. Practicing and demonstrating the full workflow of a reproduction study in the human-environment and geographical sciences, including preregistration, reproducible computational research practices, and publication of a reproduction report.

### Data collection and spatial sampling

The study exclusively uses secondary data sources. To avoid confusion, the following section will only refer to the data used for the Chicago analyses as this reproduction does not attempt to reproduce the results from the state of Illinois.

The secondary data sources are presumably complete counts of the population, health care resources, and COVID-19 cases, and thus no statistical or spatial sampling is applicable.

## Data description

The raw data necessary for our reproduction study is provided by the authors in their GitHub repository,[github.com/cybergis/COVID-19AccessibilityNotebook](https://github.com/cybergis/COVID-19AccessibilityNotebook).
However, the authors do not provide the Illinois Street Network, as it is too large for GitHub, nor do they provide the Census SVI data, presumably because they do not include this portion of this analysis in their notebook.

Covid-19 case data is derived from the Illinois Department of Public Health (IDPH).
Data was collected from the beginning of the pandemic (late February 2020) to April 10, 2020 and provides a cumulative case count.
The website, [www.dph.illinois.gov/covid19/covid19-statistics](https://www.dph.illinois.gov/covid19/covid19-statistics), is provided in the original report but has been modified as the original link returns a 404 error.
This link does not appear to provide access to archived datasets, so only the most recent case counts can be downloaded.

Hospital data was acquired from the U.S. Homeland Infrastructure Foundation Level Data (HIFLD).
The website, [www.hifld-geoplatform.opendata.arcgis.com/datasets/geoplatform::hospitals/explore](https://hifld-geoplatform.opendata.arcgis.com/datasets/geoplatform::hospitals/explore) is not provided in the original paper, but can be accessed from the provided link.
The authors filter out "military, children, psychiatric, and rehabilitation" hospitals in the study, resulting in a total of 66 hospitals for Chicago.

The Covid-19 case data were joined to zip code geographies; the authors do not specify the source of the zip code geographies in the paper but based on examination it is evident that they were derived from the U.S. Census Bureau.
The authors do not provide summary statistics in the paper but the provided dataset yields 86 zip codes for Chicago.
The authors do not provide a link for the original dataset but the ACS 2018 5-yr zip level data can be found at this website, [www.data.census.gov/cedsci/advanced?t=Age%20and%20Sex&y=2018&d=ACS%205-Year%20Estimates%20Detailed%20Tables](https://data.census.gov/cedsci/advanced?t=Age%20and%20Sex&y=2018&d=ACS%205-Year%20Estimates%20Detailed%20Tables).
Zip code shapefiles can be downloaded from this website, [www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html), or by using the census ftp, available here, [ftp2.census.gov]( ftp2.census.gov.).

Population data for the At-risk population variable were downloaded from the Census 2018 ACS 5-year estimates using the census API.
These data were joined to census tract geographies.
Again, the authors do not specify the source of the tract geographies in the paper but based on examination it is evident that they were derived from the U.S. Census Bureau.
The authors do not provide summary statistics in the paper but the provided dataset yields 878 zip codes for Chicago.
The authors do not provide a link for the original dataset but the ACS 2018 5-yr tract level data can be found at the census website, [www.data.census.gov](https://data.census.gov/cedsci/table?t=Age%20and%20Sex&y=2018&d=ACS%205-Year%20Estimates%20Detailed%20Tables&tid=ACSDT5Y2018.B01001&hidePreview=true), or automatically downloaded using the python package, [CensusData](https://pypi.org/project/CensusData/).
Tract shapefiles can be downloaded from this website, [www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html), or by using the census ftp, available here, [ftp2.census.gov]( ftp2.census.gov.).

Street network data was acquired using OSMnx, a python package that combines OpenStreetMap (OSM) data with network analysis algorithms from the python package, NetworkX.
The authors generated street networks for both Illinois and Chicago.
They did not indicate the exact date that they pulled the network, but provide a copy of the Chicago Network in their GitHub repository.
This is important because the street network is regularly updated and changed and reproducing the results exactly requires using the same street network. Full documentation of the OSMnx python package can be found at [github.com/gboeing/osmnx](https://github.com/gboeing/osmnx).

## Variables

The four variables used in this study are derived from secondary data.

- Total ICU beds
- Total ventilators per hospital
- Estimated total people age 50 or above per census tract
- Total known COVID cases per zip code

#### Attribute variable transformations

The variables are provided as totals or total estimates, and these are not transformed prior to analysis.

#### Geographic transformations

Both tract-level at risk population data and zip-code level COVID case population data are provided in their original administrative geographic scale.
These are transformed into centroids and joined to any intersecting catchment areas.

Hospital catchment area polygons are constructed by joining hospital locations to the nearest OpenStreetMap road network node, generating sets of all road network nodes within 30, 20, and 10 minute driving time, and calculating convex hulls around those nodes.
Only the temporal thresholds are reported in the journal article; while the other details are available in the computational notebook code.

The catchment areas (with the joined population + covid data) are spatially joined to a 500m hexagonal grid where any hexagon with at least half of its area covered by a catchment area.
The authors use hexagonal grids to "minimize orientation bias from edge effects."

## Analyses

The E2FSCA method is used to calculate spatial accessibility at each hexagonal location for each permutation of the two healthcare resources (ICU beds and hospital vents) to the two populations (at risk and COVID patients).
The final spatial accessibility of healthcare resources for each of the four permutations is then normalized to a score on a scale of 0 to 1, with the following equation: ```normAcc(i) = (Acc(i) - min(Acc))/(max(Acc) - min(Acc))```).

In the paper, the authors provide the results on a map using a classified color scheme.
They also provide a histogram of the distribution and the location of the mean.
In the computational notebook, they only provide code to produce the output maps with a continuous color gradient.

### Geographical characteristics

The **coordinate reference system(s)** used in the original study are not specified. While the analysis uses distance as a criteria, it is likely measured in drive time using the OSMNX package, and therefore, as long as the coordinate reference system is consistent across all layers, (re)projection should not be necessary and only considered for cartographic purposes.

The **spatial extents** of the study were both the state of Illinois and the City of Chicago (presumably the census' place defined boundaries). For our reproduction, we will only perform the analysis on the city of Chicago (OSM relation [122604](https://www.openstreetmap.org/relation/122604#map=10/41.8343/-87.7327)) excluding unpopulated tracts or zip code geographies with 0 COVID cases.

**Edge effects** are partially addressed in this analysis. When aggregating the results into accessibility grids, the authors choose to use hexagonal grids to account for directional bias of edge effects. However, when establishing their accessibility criteria scores for both Illinois and Chicago, the authors do not account for the possibility of populations that live outside the state or city seeking care within these regions.

The authors provide a framework to conduct this analysis across **multiple spatial scales**. This is evident in the use of different administrative geographies and a modifiable hexagonal output grid.  

The **spatial support** for the final analysis of spatial accessibility is a 500m hexagonal grid. The authors justify this decision based on the shortest distance between zip code centroids in Chicago: 400m.

The analysis does not include creation of any **spatial subgroups** and does not measure or account for any **first order spatial effects**, **second order spatial effects**, or **spatial anistropies**.

### Temporal characteristics

The **temporal extent** of the original study is dependent on the population and resource input variables. The COVID-19 cases represent cumulative count of COVID cases "as of April 10, 2020," but the authors do not indicate the date at which the IDPH started recording cases. The at risk population are 5 year estimates of tract populations from 2014 to 2018. The temporal extent for the hospital ventilators and ICU beds is not made explicit in the paper, but the online dataset provides a validation date for each features.

There is no temporal dimension or **temporal support** for the reproduction study.
**Temporal effects** are not measured or accounted for.

### Data exclusion

Most of the data provided in the original study's GitHub repository has already been pre-processed to deal with missing data.
The street network for Chicago has a large portion of **missing attribute data**, specifically the street speed limits. The authors make an **inference** that the average speed limit is 35mph for these missing values. This is not mentioned in the paper but can be identified in ```network_setting``` function that cleans the street network.

The study does not analyze the presence of **outliers** or exclude them.
The study does not **weight samples**.

### Analytical specification

There are no hypothesis tests requiring explanation of analytical specifications.

### Inference criteria and robustness

There are no hypothesis tests requiring explanation of inference criteria or robustness.

### Exploratory analyses and contingency planning

The entire study is an **exploratory analysis** using a parallel computing method to implement a P-E2SFCA to measure spatial accessibility of healthcare resources.
The authors do not outline any **contingency plans**.

## Reproduction study design

This reproduction study will focus on reproducing spatial accessibility results for Chicago (F7 & F8), excluding the spatial accessibility analysis for Illinois and the portion that incorporates SVI data.
The aim of this reproduction is to produce results identical to the original study.
The reproduction will use the indicators and weights as they are described in the original study.
The reproduction study will use the same software environment, using Python (3.7.6) Jupyter Notebooks in the CybgerGISX environment.
The research will be completed in full by accessing the CyberGISX environment from both Windows 10 and MacOS operating systems. Given the parallel computing processes, running these notebooks in a cyberinfrastructure environment is recommended.
Here is a list of required Python modules:

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

The study will attempt to reproduce the original methods exactly, but some deviations will be inevitable due to ambiguous information in the original article.
1. The road network used in the original analysis (or, at least in the provided notebook) was restricted to the bounds of Chicago. Thus, the original notebook does not include hospitals outside the city limits and creates a boundary effect that inaccurately portrays accessibility for Chicago. To fix this, we plan to include a 15-mi (24km) buffer that accounts for a 30-minute drive time outside of the city (at 30mph).
2. We will add code to benchmark processing time on important sections of code, for comparison with processing efficiency benchmarking in the original publication.
3. We plan to add code to produce the same classified output maps and graphs provided in the results of the original study, whereas the computational notebook generated maps with different projections and symbology from Figure 7, and did not create the graphs of Figure 8.

In addition to this, we have compiled two separate reanalysis notebooks with adjustments or improvements to the study design.
In one, we deviate from reproducing the exact results and instead aim to add improvements to the original code that we deem more appropriate for the given analysis.
In the other, we compile code to automate the pre-processing steps that the original notebook fails to include.
We believe this will facilitate a more reproducible and replicable methodology.

In the improvements notebook, we intend to:
1. Add code to summarize the road network average speeds before and after the ```network_setting``` function is run.
2. Improve the computational efficiency of the ```calculate_catchment_area``` function with two revisions: 1) Avoid creating new graphs by substituting the `ego_graph` function with the `sub_graph` function. 2) Avoid calling computationally intensive network analysis functions multiple times by using  ```nx.single_source_dijkstra_path_length``` to create a dictionary of nodes, and query those nodes to create 10, 20, and 30 minute drive-time polygons. This function will be called ```dijkstra_cca_polygons```
3. We will add options to run the code with different weighting schemes. Kang et al (2020) applied a set of weights (1.00, 0.68, & 0.22) to respective travel time zones (0-10, 10-20, & 20-30 min) to account for distance decay in their analysis. Though not explained in their methodology, these weights were likely derived from Luo & Qi's (2009) paper, which used the same E2SFCA method to assess spatial accessibility to primary care physicians in northern Illinois. In their results, Luo & Qi (2009) referenced a second weight set that represented a shaper distance decay: 1.00, 0.42, & 0.09. Another weighting scheme can be found in Delamater, Shortridge, and Kilcoyne (2019). They derive a logistic cumulative distance function, with distance decay based on distance to the nearest facility for a population, and find this to be the most accurate weight values for healthcare service distance decay: 1.0, 0.5, 0.1. Both of these weighting schemes are provided in the improvements code.

In the pre-processing notebook, we intend to automate pre-processing steps for:
- Covid-19 Cases (and corresponding zip code shapefiles)
- Tract population data (and corresponding tract shapefiles)
- Hospital data
- Chicago hexagon grid

### Evaluating the reproduction results

In order to evaluate the reproduction results, we will calculate a spearman's Rho comparing results per hexagonal location.
We expect to reject the NULL hypothesis (no correlation) and find a perfect correlation (rho = 1) between the original results and the reproduction results.
Minor differences between the original results and the reproduction results (*rho* < 1 and *p* < 0.05) will be investigated by comparing map results and discussed as possible evidence of uncertainty, error, or other internal validity problems.
Significant differences (i.e. failure to reject the NULL hypothesis with *rho* < 1 and *p* > 0.05) would constitute a failed reproduction and raise questions of internal validity requiring further investigation.

## References

Delamater, P.L., A.M. Shortridge, and R.C. Kilcoyne. 2019. Using floating catchment are (FCA) metrics to predict health care utilization patterns. BMC Health Services Research 19:144. DOI:[10.1186/s12913-019-3969-5](https://doi.org/10.1186/s12913-019-3969-5).

Kang et al. 2020. Rapidly Measuring Spatial Accessibility of COVID-19 Healthcare Resources: A Case Study of Illinois, USA. *International Journal of Health Geographics* 19:36. DOI:[10.1186/s12942-020-00229-x](https://doi.org/10.1186/s12942-020-00229-x).

Luo, W., & Qi, Y. (2009). An enhanced two-step floating catchment area (E2SFCA) method for measuring spatial accessibility to primary care physicians. *Health & place*, 15(4), 1100-1107.
