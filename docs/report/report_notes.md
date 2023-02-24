# Questions

- What is the data/derived/acc_chicago_2018_zip_pop.shp value?
- What is are the populations for the data/derived/chicago_acc.shp hospital_i and hospital_v values? Add to preanalysis plan that in comparison, just choose the better match. since the data is normalized, its nearly impossible to determine which is which...

# Original Notebook Revisions

- limit analysis & analytical options to Chicago
- organize into reproducible template structure
- report loaded package versions
- sequence code to define functions as needed, more closely following the logic/sequence of the paper methodology
- output speed limit data before/after cleaning to help check errors
- add processing time to significant analyses
- new query for OSM data to run on new package version **and to include 24140.2 buffer around Chicago**
- report which hospital catchments have been calculated as each is completed (added to `hospital_measure_acc` function)
- output results as layers in a geopackage

- Processing times using Chicago Buffer and 4 processors
- times follow these combinations: popatrisk & icubeds; popatrisk & ventilators; covidpatients & icubeds; covidpatients & ventilators
- network setting: ?, 2min 23s, 2min 6s, 1min 58s
- catchment calculation: 5min 39s, 5min 52s, 5min 57s, 5min 35s

# Reanalysis Notebook Revisions


# Future possibilities
- Permanently store a data structure of hospitals and associated catchment area geometries, rather than recalculating for different scenarios
- Use Geopandas or similar data structures to optimize spatial analysis tasks, e.g. overlay analysis or finding nearest point
- make plot distribution of results more dynamic by automatically selecting the variable (Rather than having two sections of code)
- add legends to classified results maps
