# Pre-Registration of Rpr - Reproduction of Kang et al 2020 Rapidly measuring spatial accessibility of COVID-19 healthcare resources: a case study of Illinois, USA

Joseph Holler, Department of Geography, Middlebury College, Middlebury VT 05753
Drew An-Pham, Department of Geography, Middlebury College, Middlebury VT 05753
Kufre Udoh, Department of Geography, Middlebury College, Middlebury VT 05753
Derrick Burt, Department of Geography, Middlebury College, Middlebury VT 05753

Version 1.0 | Created June 30, 2021 | Last Updated July 1, 2021

## Abstract

Kang, Michels, Lyu, Wang, Agbodo, Freeman and Wang ([2020](https://doi.org/10.1186/s12942-020-00229-x)) published a report outlining a quick and reproducible methodogy that measures and visualizes the access that two different populations, COVID-19 patients and the population risk (defined as those over 50), have to two important resources, ICU beds and Ventilators. To rapidly measure accessibility to Covid-19 healthcare, Kang et al. developed a methodology for [parallel implementation](https://www.omnisci.com/technical-glossary/parallel-computing#:~:text=Parallel%20computing%20refers%20to%20the,part%20of%20an%20overall%20algorithm.) of an Enhanced Two-Step Floating Catchment Area (E2FSCA) methodology. This method calculates the ratio between a service feature (in this scenario, hospital ICU beds or ventilators) and the population in its surrounding area, accounting for distance decay. Because this is a computationally intensive analysis hat uses large street networks, the authors developed a parallel-E2FSCA (P-E2FSCA), which enables the use of up to 4 processors while implementing the analysis.

This reproduction study is motivated by three factors. First, the impacts of COVID-19 have been severe and outlining transparent and reproducible methodologies for measuring the accessibility of healthcare resources amidst this pandemic could help us more accurately allocate life-saving resources. Second,a fully reproducible publication can be more readily replicated in new geographic, temporal, and thematic contexts, and tested for uncertainty due to data constraints and subjective modelling decisions. Third, the CyberGISX platform is a new technnology capable of making geographic research both more computationally efficient, interoperable, and accessibile; establishing standards for conducting reproducible research in this context is a vital step towards realizing these potential benefits of CyberGIS.

In this study, we attempt to identically reproduce the 2020 spatial accessibility measurements of Covid-19 healthcare resources for the city of Chicago using the Python Jupyter Notebooks in the Universiry of Illinois Urbana-Champaign CyberGISX platform. We do not attempt to reproduce the 2020 spatial accessibility measurements of Covid-19 healthcare resources for the entire state of Chicago, nor do we attempt to reproduce the social vulnerability characteristic results of high and low accessibility areas.We will compare our reproduction results with the original results using the Spearman's Rho Correlation Coefficient.

The replication study data and code will be made available in a GitHub repository to the greatest extent that licensing and file sizes permit. The reproduction will be performed entirely using the [CyberGISX platform](https://cybergisxhub.cigi.illinois.edu/) with Python (3.7.6) Jupyter Notebooks. The package specifications are outlined in the repository's procedure folder. The repository will be made public at [github.com/GIS4DEV/RPr-Malcomb-2014](https://github.com/GIS4DEV/RP-Kang).

Kang et al. 2020. Rapidly Measuring Spatial Accessibility of COVID-19 Healthcare Resources: A Case Study of Illinois, USA. *International Journal of Health Geographics* 19:36. DOI:[https://doi.org/10.1186/s12942-020-00229-x](https://doi.org/10.1186/s12942-020-00229-x).

### Keywords

CyberGIS, COVID-19, Social vulnerability, Spatial accesibility, Reproducibility, Healthcare resources

## Study design

The reproduction study design will try to implement the original study as closely as possible t reproduce the spatial accesibility measurement for Chicago (F7) and the distribution of the accessibility measure (F8). Our two confirmatory hypotheses are that we will beable to independently reproduce results for all four maps and all four histogram.

The working hypothesis are:

> H1: There is no correlation between Kang et al's spatial accessibility measurement of healthcare resources in Chicago and our reproduction study's spatial accessibility measurement of healthcare resources in Chicago.

> H2: There is no correlation between Kang et al's distribution of accessibility measurement of healthcare resources in Chicago and our reproduction study's distribution of accessibility of healthcare resources in Chicago.


### Original study design


The original study is **observational** and **descriptive**, with no hypotheses or effect sizes.

The study measures the spatial accessibility of a single healthcare resource (ICU beds or ventilators) to a single population (At-risk or Covid-19 patients).

The **spatial extents** of the study were the state of Illinois and the city of Chicago (separate analyses). We will only reproduce the results for Chicago.
The **spatial scales** of the analysis were variable dependent. The at-risk population data were measured at the census tract level geography . The Covid-19 cases were measured at the zip code level geography. The final results were reaggregated in 500-meter hexagonal grids.
The **temporal extent** of the study was also variable dependent. The Covid-19 was a cumulative case count from the begginning of collection (~late Feb 2020-Apr 10,2020). The ACS population and geographic data was collected in 2018.

There is no **randomization** in the original study.

**GO FURTHER INTO STUDY DESIGN**

The study was originally conducted in CyberGIS Jupyter Notebooks using Python (3.7.6). The original study materials can be found at [https://github.com/cybergis/COVID-19AccessibilityNotebook](https://github.com/cybergis/COVID-19AccessibilityNotebook). It should be noted that this repository does not cover the paper's entire methodology.


## Sampling plan

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

Covid-19 case data is derived from Illinois Depart of Public Health (IDPH). Data was collected from the beginning of the pandemic (late February 2020) to April 10, 2020 and provides a cumulative case count. The authors report a cumulative case counnt of 7600 confirmed cases for Chicago used in the the study.

Hospital data was acquired from the U.S. Homeland Infrastructure Foundation Level Data (HIFLD). The authors filter out "military, children, psychiatric, and rehabilitation" hospitals in the study, resulting in a total of 66 hospitals for Chicago.

The Covid-19 case data were joined to zip code geographies; the authors do not specify the source of the zip code geographies in the paper but based on examination it is evident that they were derived from the U.S. Census Bureau. The authors do not provide summary statistics in the paper but the provided dataset yields 86 zip codes for Chicago.

Population data for the At-risk population variable were pulled from the Census 2018 ACS 5-year estimates using a census API key. These data were joined to census tract geographies. Again, the authors do not specify the source of the tract geographiees in the paper but based on examination it is evident that they were derived from the U.S. Census Bureau. The authors do not provide summary statistics in the paper but the provided dataset yields 878 zip codes for Chicago.

Street network data was provided by OSMNX, a python package that combines OSM data with network analysis algorithms from the pythonn package, NetworkX. The authors pull a street network for both Illinois and Chicago. Theydo not indicate the exact date that they pulled the network, but provide a copy of the Chicago Network in their notebook. This is important because the street network is regularly updated and changed and reproducing the results exactly requires using the same street network.



## Variables



#### Attribute variable transformations


#### Geographic transformations


## Analyses


### Geographical characteristics


### Temporal characteristics


### Data exclusion


### Analytical specification


### Inference criteria and robustness



### Exploratory analyses and contingency planning


## Reproduction study design

### Planned differences from the original study


### Evaluating the reproduction results


## Referencing the original paper


### Sections



### Tables, figures, other elements



## Other references

