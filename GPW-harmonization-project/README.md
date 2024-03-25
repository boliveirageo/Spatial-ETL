

# Integrated Approach to Global Land Use and Land Cover Data Harmonization
[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC_BY--SA_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

This project outlines the process of harmonizing global reference samples and EO/gridded datasets, aligning them with GPW classes for optimized integration into the GPW machine learning workflow.
.
This work is licensed under a
[Creative Commons Attribution-ShareAlike 4.0 International License][cc-by-sa].


**Note**: This work currently focuses on vector data in GeoPackage and GeoParquet formats.

**For any questions, please refer to our [FAQs](https://github.com/maja601/EuroCrops/wiki/FAQs) or use the Discussions/Issues to reach out to us.**

***
## Content

1. [Workflow](#workflow)
2. [Harmonization data](#harmonization)
3. [Ontology Guideline] (#ontology_guideline)
4. [Datasets used](#datasets_used)
5. [GitHub project structure](#github_structure)
7. [Data Download](#data_download)
8. [Reference](#reference)


***
## Workflow <a name="workflow"></a>
![g1924](figures/workflow-dataprocessing.png)


## Harmonization data <a name="harmonization"></a>
We focused on reference samples derived from visual interpretation with a minimum spatial support of 30 meters (Landsat and Sentinel resolution). These samples represent LULC classes for points or regions. An automated script (Python, R, or Jupyter Notebook) was developed for each dataset to:

- Download vector files.
- Convert existing LULC classes into corresponding Global Pasture Watch (GPW) classes:
      - Seeded grass
      - Natural or semi-natural grass
      - Other
- Assign weights to samples based on their level of mixture (explained in the project).
- Generate a harmonized output table with the following columns:
      - dataset_name: Name of the original dataset (LULC)
      - reference_year: Reference year of the samples in the original dataset
      - original_lulc_class: Original land use and land cover class name
      - gpw_lulc_class: GPW land use and land cover class name
      - sample_weight: Weight assigned to the sample

The land use and land cover (LULC) classes from the original databases were associated to the GPW project's classes using definitions from the original databases and the following ontology as guideline: 

This example the column in output harmonization data


| Attribute Name | Definition                                                |
| -------------- | ----------------------------------------------------------- |
| dataset_name     | The name of original dataset LULC|
| reference_year | The reference year of samples the orginal dataset.|
| original_lulc_class      | Name classe land use and land cover the original dataset. |
| gpw_lulc_class      | Name classe land use and land cover the Global Pasture Watch project. |
| sample_weight      | The sample weight   |


***
## Ontology Guideline <a name="ontology_guideline"></a>

The ontology guideline provides a standardized classification framework for LULC classes. Here's a breakdown of the GPW classes used in this project, along with corresponding descriptions and examples:

| level	| label	| class	| description	| examples	| gpw class |
| 5	| GRASSLAND	| landcover	| Land (and the vegetation growing on it) devoted to the production of introduced or indigenous forage for harvest by grazing, cutting, or both. Usually managed to arrest successional processes. The term ‘grassland’ is synonymous with pastureland when referring to an imposed grazing-land ecosystem. | The vegetation of grassland in this context is broadly interpreted to include grasses, legumes and other forbs, and at times woody species may be present 		| na |
| 5.1	| Annual grassland	| landuse	| Forage is established annually, usually with annual plants, and generally involves soil disturbance, removal of existing vegetation, and other cultivation practices |  | 2 |
| 5.2	| Campos	| landcover	| Grassland consisting mainly of grasses, along with herbs, small shrubs and occasional trees; on undulating and hilly landscape, with variable soil fertility. Differs from Cerrado in having a longer and more severe winter and a relative abundance of native legumes. | Northern part of the Pampa. The sub-tropical climate is humid, warm in summer and mild in winter. | 1 |
| 6	MOSAIC	| landcover | Mosaic of agricultural areas with natural vegetation (e.g., tree cover, shrub cover) |  | 0 | 
| 7	SHRUBLAND / SCRUB-FILED | landcover	| Land on which the vegetation is dominated by low-growing woody plants. Areas covered by trees with a canopy closure of at least 10%. Also woody hedges and palm trees are included in this class. With sparse tree cover or without tree cover |  | na |
7.1	Undisturbed woodland	landcover	Land covered by woody vegetation higher than 5 meters that is unmanaged, where the ecological processes are not significantly disturbed		0

Full ontology available on the following link: https://docs.google.com/spreadsheets/d/1rRbM63flbizg6eP0PtogePM4K6ZnEDoFauCrV3TxZtA/edit?usp=sharing

## Datasets used <a name="Datasets_used"></a>

This project utilized the following datasets:
- CONUS Validation Samples (U.S.) (https://www.usgs.gov/special-topics/lcmap/lcmap-conus-reference-data)
- MapBiomas Samples (Brazil) (https://zenodo.org/)
- LUCAS Samples (Europe) (https://insitu.copernicus.eu/news/getting-to-know-lucas-the-land-use-land-cover-area-frame-survey)
- GeoWiki Samples (Global) (https://doi.pangaea.de/)
- PREDICTS Database Samples (Global) (Link to be replaced with the correct one)
- WorldCereal Samples (Global) (https://about.zenodo.org/principles/)
- DynamicWorld Samples (Global) (https://www.learner.org/wp-content/interactive/dynamicearth/drift2.html)
- CropHarvest Samples (Global) (https://github.com/nasaharvest/cropharvest)
- EuroCrops Samples (https://github.com/maja601/EuroCrops)


## GitHub project structure <a name="github_structure"></a>
```
├── ipynb
│   └── Code in Jupyter notebook format (Python)
├── original_database
│   └── Links to original databases
├── harmonized_datasets
   └── data_processed_qa
     └── vector_data
        ├── parquet
          └── Link to parquet file
        └── geopackage
          └── Link to geopackage file
   └── raw_data  (to be included in future updates)
     ├── raster_data  (to be included in future updates)
     └── vector_data  (to be included in future updates)
        ├── parquet  (to be included in future updates)
          └── Link to parquet file  (to be included in future updates)
        └── geopackage  (to be included in future updates)
          └── Link to geopackage file  (to be included in future updates)
```

## Data Download<a name="data_download"></a>

The processed vector data is currently available via Google Drive [google drive de project](). A download link will be added here in the future.

## References<a name="references"></a>

**Disclaimer**: Please reference the dataset dependent source in case you're using their data.


[![CC BY-SA 4.0][cc-by-sa-image]][cc-by-sa]

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-image]: https://licensebuttons.net/l/by-sa/4.0/88x31.png
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg
