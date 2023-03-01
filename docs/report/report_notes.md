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
- must use buffered street network! The provided network has disjoint areas and edge effects
- classify results for mapping, and map in style more similar to the publication
- graph statistical distribution of results with histograms as in the publication
- calculate population centroids in data section, and do not recalculate them for each scenario
- improve markdown narrative and code comments for legibility
- add metadata

# Reanalysis Revisions
(in addition to original notebook revisions)

- calculate catchment areas by creating one set of nodes within 30m drive time and selecting 20m and 10m sets from the 30m set by attribute, rather than creating three ego_graphs
- add option to run analysis on a small subset of hospitals
- change default speed limit for roads to 30 mph (the urban speed limit for Illinois)

## Types of Edge effects

- Hospitals "snap" to nearest node in network
- Disjoint networks at edges (e.g. O'Hare airport area)
- Hospitals within 30 minutes of study extent should be included
- Populations within 60 minutes of study extent should be included (since they may use the same hospital as populations at edge of the study area)

Remember the original notebook was meant to use the whole Illinois network for all analyses, and for good reason.

- using only Chicago data gives results closer to the Original results; save switching to Illinois population data for the reanalysis

## Processing Times (4 processors)

| Network | Code Version | Population | Service | Setup Time | Catchment Time |
| -- | -- | -- | -- | -- | -- |
| No Buffer | Replication | >50 | Beds | 0:33 | 2:21 |
| No Buffer | Replication | >50 | Ventilators | 0:32 | 2:23 |
| No Buffer | Replication | Covid | Beds | 0:18 | 2:12
| No Buffer | Replication | Covid | Ventilators | 0:18 | 2:12
| Buffer | Replication | >50 | Beds | 1:38 | 5:49 , 6:01, 5:43, 5:38 |
| Buffer | Replication | >50 | Ventilators | 1:41 | 5:52, 6:14 |
| Buffer | Replication | Covid | Beds | 1:30 | 5:36, 5:50
| Buffer | Replication | Covid | Ventilators | 2:07 | 5:39, 5:49
| Buffer | Reanalysis | >50 | Beds | ? | 1:42 |
| Buffer | Reanalysis | >50 | Ventilators | ? | ? |
| Buffer | Reanalysis | Covid | Beds | ? | ?
| Buffer | Reanalysis | Covid | Ventilators | ? | ?


# Reanalysis Notebook Revisions


# Future possibilities
- Permanently store a data structure of hospitals and associated catchment area geometries, rather than recalculating for different scenarios
- Use Geopandas and spatial indexing to optimize spatial analysis tasks, e.g. overlay analysis or finding nearest point
- make sure geopackage layer outputs only contain the recently calculated field (i.e. icu_beds OR vents, but not both)
- use `osmnx.speed()` function to improve speed data
- use `osmnx.graph` function's `simplify` option to simplify the graph, rather than the network setting procedure
- apply 55mph speed limit to highways (the urban speed limit in Illinois)
- joining hospitals to street network takes 1:16. Could this be faster with geopandas?
- normalizing the results makes it more difficult to compare... do they need to be normalized?
- use area-weighted reaggregation rather than centroids
- uncertainties using convex hull for generating catchment area polygons
