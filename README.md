# Template for Reproducible and Replicable Research
This repository is based on a template that contains a folder structure, template documents, and suggestions for best practices for conducting reproducible geographic research. The folder structure presented here can be used to:

1. pre-register, document, and share original research, or
2. document, organize, and share a reproduction and/or replication of original research.

An overview of the folder structure of this repository is provided below. The `README.md` and `index.csv` files contained in each folder provide details about the structure of that folder and suggestions on its use. The `docs/report/` folder contains templates to facilitate 1) the pre-registration of original research, and 2) report the complete details of attempted reproductions and replications of original research.

## Repository Overview

    Reproduction of <Study Name>
    |- docs/           # study documentation
    |  +- report/      # reproduction plan, reproduction report
    |  +- manuscript/  # manuscript components
    |
    |- data            # raw data, which are not changed once created
    |  +- raw/         # raw data, will not be altered
    |  +- derived/     # derived data, will not be altered once created
    |  +- scratch/     # temporary files that can be safely deleted or lost
    |  +- metadata/    # documentation of metadata
    |
    |-procedure
    |  +- code/        # any programmatic code, clearly named and commented
    |  +- protocols/   # any non-computational protocols
    |  +- environment/ # information about the required hardware / software computational environment
    |
    |- results         # all output from workflows and analyses
    |  +- figures/     # figures, graphs, and maps, likely designated for manuscript or presentations
    |  +- other/       # other media outputs resulting from the research
    |  +- tables       # maps, likely designated for manuscript  
    |- readme.md       # the top level description of content
    |- Makefile        # executable Makefile, if applicable
    |- study.Rproj     # RStudio project, if applicable

## Reproducible Research Practices
Every research project is different. This repository is designed to serve as a flexible guide capable of structuring work completed throughout the lifecycle of different types of research project. No matter the project type, a few key suggested practices when using this repository include:

- Keeping original, raw data in the `data/raw` folder. Do not alter that file during data analysis.
- Keeping data derived from the raw data (e.g. subsets) separate from the raw data in the `data/derived` folder.
- Keeping Exploratory/experimental outputs in the `data/Scratch` folder. *Files in this folder should be able to be deleted without negatively impacting the project*.  
- Limiting manual changes to data. *Conduct as much data processing and analysis as possible with code*.
- Keeping code in simple text files that are human readable.
- Explicitly tying procedural documents or code together so it is clear how things work together
- Creating a top-level `Makefile` or Rmarkdown file that documents computational work in executable form.
- Providing a executable electronic research compendia that shares the entire computational environment
- Keeping a README in each folder, describing the purpose of the directory and its contents.
- Maintaining a formal metadata descriptor at the root of the package that describes all the important input and output data files.

## References
The structure of this repository closely follows the excellent [rr-init](https://github.com/Reproducible-Science-Curriculum/rr-init) repository, which in turn follows Nobel [(2009)](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1000424). We have also incorporated structural ideas from [Gandrud (2015)](http://christophergandrud.github.io/RepResR-RStudio/) and Camerer et al. ([2016](https://osf.io/pfdyw/), [2018](https://osf.io/bzm54/)).  Reference information related to the **Pre-registration Template** and **Replication Report Template** is included in the `/docs` folder.

## Repository Template Citation and License
This research compendium template is in its testing phase. It will eventually be published to the public with an open-source license at
https://github.com/HEGSRR/RR-Template
The compendium is the work of Peter Kedron, Joseph Holler, and Zach Hilgendorf. 
This draft version of the compendium is provided for private use only: not for distribution.

# Original Accessibility Notebook readme.md Content

> The content below was the root `readme.md` document for the Where COVID-19 Accessibility notebook. Some of this content should be moved to the `metadata.csv` file.

[![CyberGISX](results/figures/original/CyberGISXLogo.svg)](https://cybergisxhub.cigi.illinois.edu/)

# Spatial Accessibility to ICU Beds and Ventilators in Illinois

<div>
    <img src="results/figures/original/ChicagoResult.png" height="450" width="350"/>
    <img src="results/figures/original/IllinoisResult.png" height="450" width="350"/>
</div>

**Authors:** Jeon-Young Kang, Alexander Michels, Fangzheng Lyu, Shaohua Wang, Nelson Agbodo, Vincent L. Freeman & Shaowen Wang

**Paper:** https://doi.org/10.1186/s12942-020-00229-x

**Abstract:** This aims to measure spatial access for people to hospitals in Illinois. The spatial accessibiilty is measured by the use of an enhanced two-step floating catchment area (E2FCA) method (Luo & Qi, 2009), which is an outcome of interactions between demands (i.e, # of potential patients; people) and supply (i.e., # of beds or physicians). The result is a map of spatial accessibility to hospital beds. It identifies which regions need more healthcare resources, such as the number of ICU beds and ventilators. This notebook serves as a guideline of which areas need more beds in the fight against COVID-19.

To view accessibility measures updated daily, check out: https://wherecovid19.cigi.illinois.edu/


## What's Inside

A quick explanation of the components:

* `COVID-19Acc.ipynb` is a notebook for calculating spatial accessibility and `COVID-19Acc.html` is an export of the notebook as HTML.
* `Data` contains all of the data necessary for calculations:
  * `Chicago_Network.graphml`/`Illinois_Network.graphml` are GraphML files of the OSMNX street networks for Chicago and Illinois respectively.
  * `GridFile/` has hexagonal gridfiles for Chicago and Illinois
  * `HospitalData/` has shapefiles for the hospitals in Chicago and Illinois
  * `IL_zip_covid19/COVIDZip.json` has JSON file which contains COVID cases by zip code from IDPH
  * `PopData/` contains population data for Chicago and Illinois by census tract and zip code.
  * `Result/` is where we write out the results of the spatial accessibility measures
  * `SVI/`contains data about the Social Vulnerability Index (SVI)
* `img/` contains some images and HTML maps of the hospitals (the notebook generates the maps)
* `README.md` is the document you're currently reading!
* `requirements.txt` is a list of Python packages necessary to use the notebook (besides Jupyter/IPython). You can install the packages with `python3 -m pip install -r requirements.txt`

```
> tree ./

├── COVID-19Acc.html
├── COVID-19Acc.ipynb
├── Data
│   ├── Chicago_Network.graphml
│   ├── GridFile
│   │   ├── Chicago_Grid.cpg
│   │   ├── Chicago_Grid.dbf
│   │   ├── Chicago_Grid.prj
│   │   ├── Chicago_Grid.qpj
│   │   ├── Chicago_Grid.shp
│   │   ├── Chicago_Grid.shx
│   │   ├── Illinois_Grid.cpg
│   │   ├── Illinois_Grid.dbf
│   │   ├── Illinois_Grid.prj
│   │   ├── Illinois_Grid.qpj
│   │   ├── Illinois_Grid.shp
│   │   └── Illinois_Grid.shx
│   ├── HospitalData
│   │   ├── Chicago_Hospital_Info.cpg
│   │   ├── Chicago_Hospital_Info.dbf
│   │   ├── Chicago_Hospital_Info.prj
│   │   ├── Chicago_Hospital_Info.qpj
│   │   ├── Chicago_Hospital_Info.shp
│   │   ├── Chicago_Hospital_Info.shx
│   │   ├── Illinois_Hospital_Info.cpg
│   │   ├── Illinois_Hospital_Info.dbf
│   │   ├── Illinois_Hospital_Info.prj
│   │   ├── Illinois_Hospital_Info.qpj
│   │   ├── Illinois_Hospital_Info.shp
│   │   └── Illinois_Hospital_Info.shx
│   ├── Illinois_Network.graphml
│   ├── IL_zip_covid19
│   │   └── COVIDZip.json
│   ├── PopData
│   │   ├── Chicago_Tract.cpg
│   │   ├── Chicago_Tract.dbf
│   │   ├── Chicago_Tract.prj
│   │   ├── Chicago_Tract.qpj
│   │   ├── Chicago_Tract.shp
│   │   ├── Chicago_Tract.shx
│   │   ├── Chicago_ZIPCODE.cpg
│   │   ├── Chicago_ZIPCODE.dbf
│   │   ├── Chicago_ZIPCODE.prj
│   │   ├── Chicago_ZIPCODE.qpj
│   │   ├── Chicago_ZIPCODE.shp
│   │   ├── Chicago_ZIPCODE.shx
│   │   ├── Chicago_ZIPCODE_UTM.cpg
│   │   ├── Chicago_ZIPCODE_UTM.dbf
│   │   ├── Chicago_ZIPCODE_UTM.prj
│   │   ├── Chicago_ZIPCODE_UTM.shp
│   │   ├── Chicago_ZIPCODE_UTM.shx
│   │   ├── CovidCase.csv
│   │   ├── COVIDZip.json
│   │   ├── elderly_tract_IL.csv
│   │   ├── Illinois_Tract.cpg
│   │   ├── Illinois_Tract.dbf
│   │   ├── Illinois_Tract.prj
│   │   ├── Illinois_Tract.qpj
│   │   ├── Illinois_Tract.shp
│   │   ├── Illinois_Tract.shx
│   │   ├── Illinois_ZIPCODE.cpg
│   │   ├── Illinois_ZIPCODE.dbf
│   │   ├── Illinois_ZIPCODE.prj
│   │   ├── Illinois_ZIPCODE.qpj
│   │   ├── Illinois_ZIPCODE.shp
│   │   ├── Illinois_ZIPCODE.shx
│   │   └── zipcode_pop_illinois.csv
│   ├── Result
│   │   ├── ACC_Chicago_2018_ZIP_POP.cpg
│   │   ├── ACC_Chicago_2018_ZIP_POP.dbf
│   │   ├── ACC_Chicago_2018_ZIP_POP.prj
│   │   ├── ACC_Chicago_2018_ZIP_POP.shp
│   │   ├── ACC_Chicago_2018_ZIP_POP.shx
│   │   ├── Chicago_ACC.cpg
│   │   ├── Chicago_ACC.dbf
│   │   ├── Chicago_ACC.prj
│   │   ├── Chicago_ACC.shp
│   │   ├── Chicago_ACC.shx
│   │   ├── Illinois_ACC.cpg
│   │   ├── Illinois_ACC.dbf
│   │   ├── Illinois_ACC.prj
│   │   ├── Illinois_ACC.shp
│   │   └── Illinois_ACC.shx
│   └── SVI
│       ├── SVI2018_ILLINOIS_tract.cpg
│       ├── SVI2018_ILLINOIS_tract.dbf
│       ├── SVI2018_ILLINOIS_tract.prj
│       ├── SVI2018_ILLINOIS_tract.sbn
│       ├── SVI2018_ILLINOIS_tract.sbx
│       ├── SVI2018_ILLINOIS_tract.shp
│       ├── SVI2018_ILLINOIS_tract.shp.xml
│       └── SVI2018_ILLINOIS_tract.shx
├── img
│   ├── Chicago_hospitals_interactive_map.html
│   ├── ChicagoResult.png
│   ├── Illinois_hospitals_interactive_map.html
│   ├── IllinoisResult.png
│   └── method.png
├── README.md
└── requirements.txt

8 directories, 92 files
```
