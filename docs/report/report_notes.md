# Questions

- we have used data/derived/chicago_acc.shp as the original results, but those results cannot be recomputed with the current notebook / repository.

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
- must use buffered street network! notebook dijoint areas and edge effects with provided street network

## Types of Edge effects

- Hospitals "snap" to nearest node in network
- Disjoint networks at edges (e.g. O'Hare airport area)
- Hospitals within 30 minutes of study extent should be included
- Populations within 60 minutes of study extent should be included (since they may use the same hospital as populations at edge of the study area)

Remember the original notebook was meant to use the whole Illinois network for all analyses, and for good reason.

## Processing Times (4 processors)

| Network | Code Version | Population | Service | Setup Time | Catchment Time |
| -- | -- | -- | -- | -- | -- |
| No Buffer | Replication | >50 | Beds | 0:33 | 2:21 |
| No Buffer | Replication | >50 | Ventilators | 0:32 | 2:23 |
| No Buffer | Replication | Covid | Beds | 0:18 | 2:12
| No Buffer | Replication | Covid | Ventilators | 0:18 | 2:12
| Buffer | Replication | >50 | Beds | ? | ? |
| Buffer | Replication | >50 | Ventilators | 2:23 | 5:52 |
| Buffer | Replication | Covid | Beds | 2:06 | 5:57
| Buffer | Replication | Covid | Ventilators | 1:58 | 5:35


# Reanalysis Notebook Revisions


# Future possibilities
- Permanently store a data structure of hospitals and associated catchment area geometries, rather than recalculating for different scenarios
- Use Geopandas or similar data structures to optimize spatial analysis tasks, e.g. overlay analysis or finding nearest point
- make plot distribution of results more dynamic by automatically selecting the variable (Rather than having two sections of code)
- make sure geopackage layer outputs only contain the recently calculated field (i.e. icu_beds OR vents, but not both)
