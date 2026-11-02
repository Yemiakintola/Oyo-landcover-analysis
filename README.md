# Oyo-landcover-analysis
# Oyo State Land Cover Change Analysis and 2031 Projection

### Geospatial Data Science | Remote Sensing | Machine Learning | Google Earth Engine

**Author:** Akinyemi Akintola  
**Project Area:** Oyo State, Nigeria  
**Project Focus:** Land Cover Classification, Change Detection, and Future Land Cover Projection  
**Technologies:** Python, Google Earth Engine, Google Colab,  Raster Analysis, Machine Learning


## 1. Project Overview

Land cover change is an important indicator of environmental transformation, urban expansion, vegetation loss, and pressure on natural resources. Understanding these changes is essential for sustainable urban planning, environmental monitoring, agricultural development, and evidence-based policymaking.

This project investigates land cover dynamics across Oyo State, Nigeria, using satellite remote sensing, geospatial analysis, and machine learning techniques.

The project aims to classify land cover at selected historical intervals, quantify transitions between land cover classes, and develop a spatial projection of potential land cover patterns for 2031.

The workflow combines satellite imagery, terrain information, spectral indices, and machine learning to examine the distribution and transformation of four major land cover classes:

- **Vegetation:** Areas dominated by vegetation, including cultivated land and other vegetated surfaces, subject to the classification scheme.
- **Bare Soil:** Exposed soil and other predominantly unvegetated land surfaces.
- **Urban/Built-up:** Developed areas dominated by buildings, roads, and other constructed surfaces.
- **Water:** Rivers, reservoirs, ponds, and other identifiable water bodies.

The overall objective is to generate useful geospatial evidence that can support land management, environmental planning, and future research in Oyo State.

## 2. Project Objectives

The principal objectives are to:

1. Map the spatial distribution of major land cover classes in Oyo State.
2. Produce land cover classifications for selected historical years.
3. Identify locations where land cover has changed over time.
4. Quantify transitions between vegetation, bare soil, urban areas, and water.
5. Investigate patterns of urban expansion and vegetation change.
6. Develop a potential 2031 land cover projection using a Markov-chain-based transition model and spatial allocation techniques.
7. Demonstrate the application of geospatial data science and machine learning to environmental monitoring.

## 3. Study Area

The study area is Oyo State, located in southwestern Nigeria.

The analysis uses administrative boundary data to define the Area of Interest (AOI). The boundary is used to constrain satellite imagery, classification, spatial statistics, and map production to the study region.

**Study area:** Oyo State, Nigeria  
**Geographic region:** Southwestern Nigeria  
**Boundary source:** Administrative boundary dataset used in the project workflow

The quality of the results depends on the accuracy and suitability of the administrative boundaries, satellite observations, training samples, and classification methods.

## 4. Data Sources

The project uses satellite imagery and complementary geospatial datasets.

| Dataset | Application |
|---|---|
| Sentinel-2 satellite imagery | Land cover classification and change detection |
| Digital Elevation Model (SRTM) | Terrain characteristics and topographic context |
| Spectral indices | Distinguishing vegetation, water, built-up areas, and exposed soil |
| Administrative boundaries | Defining the study area and clipping outputs |
| Training samples | Providing labelled examples for supervised classification |

### Sentinel-2 Imagery

Sentinel-2 imagery provides multispectral observations suitable for vegetation monitoring, surface analysis, and land cover mapping.

The workflow uses relevant visible, near-infrared, and shortwave-infrared bands to support discrimination between land cover classes.

### Terrain Data

Elevation and slope derived from the Shuttle Radar Topography Mission (SRTM) Digital Elevation Model may be incorporated as additional classification predictors.

### Spectral Indices

The workflow incorporates commonly used spectral indices, including:

- **NDVI (Normalized Difference Vegetation Index):** Helps identify and characterise vegetated surfaces.
- **MNDWI (Modified Normalized Difference Water Index):** Helps distinguish water bodies from surrounding surfaces.
- **NDBI (Normalized Difference Built-up Index):** Helps identify built-up surfaces.
- **BSI (Bare Soil Index):** Helps identify exposed soil and other predominantly bare surfaces.

These indices are complementary indicators rather than definitive labels. Their effectiveness depends on local land cover conditions, image quality, seasonal effects, and the classification model.

## 5. Methodology

The project follows a structured geospatial workflow.

### Stage 1: Study Area Preparation

The administrative boundary dataset is loaded into the geospatial environment and used to define the AOI.

The study boundary is checked for spatial consistency before satellite imagery is processed.

### Stage 2: Satellite Image Collection and Preprocessing

Sentinel-2 imagery is accessed through Google Earth Engine.

The preprocessing workflow is designed to:

- Filter imagery by the required dates and study area.
- Apply cloud and cloud-shadow masking.
- Select relevant spectral bands.
- Generate suitable image composites.
- Calculate spectral indices.
- Incorporate terrain variables where appropriate.

Seasonal consistency is important because vegetation condition, soil exposure, and water extent can vary considerably throughout the year.

### Stage 3: Feature Engineering

Relevant spectral bands, derived indices, and terrain variables are combined into a predictor dataset.

These predictors provide complementary information for distinguishing the four target land cover classes.

### Stage 4: Supervised Land Cover Classification

A Random Forest classifier is used in the proposed classification workflow.

Random Forest is an ensemble machine learning algorithm that combines predictions from multiple decision trees. It is widely used in remote sensing because it can model nonlinear relationships between spectral predictors and land cover classes.

The classification workflow involves:

1. Preparing labelled training samples.
2. Extracting predictor values for the samples.
3. Dividing the samples into training and validation subsets.
4. Training the classifier.
5. Applying the trained model to the satellite composite.
6. Generating a categorical land cover map.

Classification quality should be evaluated using independent validation samples and appropriate metrics, including overall accuracy, class-specific precision and recall, and a confusion matrix where available.

### Stage 5: Land Cover Change Detection

The classified maps are compared across selected historical periods.

The change detection process is designed to identify transitions such as:

- Vegetation to urban/built-up.
- Vegetation to bare soil.
- Bare soil to urban/built-up.
- Urban/built-up to vegetation.
- Changes involving water bodies.

A transition matrix can be used to summarise the area moving from each initial class to each subsequent class.

This helps distinguish the overall extent of change from the specific types of transitions occurring across the study area.

### Stage 6: Land Cover Projection for 2031

The project investigates a future land cover scenario using a Markov-chain-based transition model and spatial allocation.

The Markov component estimates transition probabilities from observed land cover changes between historical maps.

The spatial allocation component assigns projected transitions to locations using the selected spatial rules and neighbourhood information.

The resulting projection represents a modelled future scenario, not a definitive prediction of what the landscape will look like in 2031.

Its reliability depends on the accuracy of the historical classifications, the suitability of the transition probabilities, the spatial allocation assumptions, and the extent to which past patterns remain relevant.

### Stage 7: Map Production and Visualisation

The final workflow produces thematic maps and supporting spatial outputs.

The intended map categories are:

| Land cover class | Display colour |
|---|---|
| Vegetation | Green |
| Bare Soil | Yellow |
| Urban/Built-up | Red |
| Water | Blue |

Maps are designed to support comparison between historical periods and the projected 2031 scenario.

QGIS may be used for cartographic refinement, layout preparation, and export of publication-ready maps.

## 6. Technology Stack

| Technology | Role |
|---|---|
| Python | Data processing, analysis, and workflow automation |
| Google Colab | Cloud-based Python development |
| Google Earth Engine | Satellite imagery access and geospatial processing |
| Sentinel-2 | Multispectral satellite observations |
| Random Forest | Supervised land cover classification |
| NumPy and Pandas | Numerical computation and tabular analysis |
| Rasterio | Raster data processing, where required |
| GeoPandas | Vector data processing, where required |
| Matplotlib | Data visualisation |
| QGIS | Cartography and geospatial visualisation |

The exact libraries and versions depend on the implementation used in each notebook.

## 7. Repository Structure

The repository is intended to follow a structure similar to the one below.

```text
oyo-landcover-analysis/
│
├── README.md
├── LICENSE
├── .gitignore
├── requirements.txt
├── DATA_SOURCES.md
│
├── notebooks/
│   ├── landcover_classification.ipynb
│   ├── change_detection.ipynb
│   └── landcover_projection_2031.ipynb
│
├── scripts/
│   └── preprocessing.py
│
├── maps/
│   ├── landcover_2018.png
│   ├── landcover_2019.png
│   ├── landcover_2020.png
│   ├── landcover_2021.png
│   ├── landcover_2022.png
│   ├── landcover_2023.png
│   ├── landcover_2024.png
│   ├── landcover_2025.png
│   └── projection_2031.png
│
└── docs/
    └── methodology.md
```

This is a suggested structure. Files should only be added to the repository when they exist and are ready to share.

Large satellite rasters, temporary processing files, credentials, and restricted datasets should be excluded from the public repository.

## 8. How to Access and Reproduce the Project

### Step 1: Open the repository

Visit this project's GitHub repository: https://github.com/Yemiakintola/Oyo-landcover-analysis and review the notebooks and documentation.

### Step 2: Open a notebook in Google Colab

Open the selected `.ipynb` file in Google Colab.

### Step 3: Configure Google Earth Engine

If the notebook uses Google Earth Engine, authenticate your Google account and initialise Earth Engine with an authorised Google Cloud project.

For example:

import ee

ee.Authenticate()
ee.Initialize(project="YOUR_GOOGLE_CLOUD_PROJECT_ID")

Replace the placeholder with your own authorised project ID.

### Step 4: Configure the study area

Update the notebook's asset configuration to point to an accessible administrative boundary dataset.

Private Earth Engine assets used during development are not automatically made available to other users through GitHub.

### Step 5: Install dependencies

If a `requirements.txt` file is provided, install the listed packages in the intended environment.

```python
%pip install -r requirements.txt
```

Some packages may already be installed in Google Colab. Version compatibility should be checked before upgrading dependencies.

### Step 6: Run the analysis

Follow the notebook cells in order, starting with authentication, configuration, and data preparation.

Processing requirements depend on the study area, imagery, sample size, and output resolution.

**Reproducibility note:** A complete reproduction requires access to the source datasets, Earth Engine assets, training samples, and any external services referenced by the notebooks.

## 9. Expected Outputs

The project workflow is designed to produce:

- Historical land cover classification maps.
- Spatial summaries of land cover distribution.
- Land cover transition matrices.
- Maps of land cover changes between observation periods.
- A modelled land cover scenario for 2031.
- Supporting statistics and visualisations.

Quantitative findings, classification accuracy values, and projected area estimates should be reported only after they have been calculated and validated.

## 10. Applications and Significance

The project has potential applications in several areas.

### Urban and Regional Planning

Land cover change analysis can help planners investigate patterns of urban expansion and the conversion of undeveloped land to built-up areas.

### Environmental Management

Changes in vegetation and exposed soil may help identify areas requiring further environmental investigation.

### Agricultural Planning

Land cover maps can provide contextual information for agricultural assessment and landscape monitoring.

### Flood and Watershed Studies

The distribution of built-up areas, vegetation, bare soil, and water can provide useful inputs to broader hydrological and flood-risk investigations. Land cover maps alone, however, are not sufficient to establish flood risk.

### Research and Education

The project demonstrates how remote sensing, machine learning, and geospatial analysis can be combined to investigate environmental change.

## 11. Limitations

The results must be interpreted in light of the following limitations:

1. **Classification uncertainty:** Spectrally similar land cover types may be misclassified.
2. **Cloud contamination:** Residual clouds and shadows may affect satellite composites.
3. **Seasonal differences:** Changes in observation dates can create apparent changes unrelated to actual land cover conversion.
4. **Training data quality:** Inaccurate or unrepresentative training samples can reduce classification reliability.
5. **Spatial resolution:** Mixed land cover within individual pixels can complicate classification.
6. **Projection uncertainty:** Future land cover patterns depend on historical transition rates and spatial allocation assumptions.
7. **Data accessibility:** Reproduction may require separate access to external datasets and Google Earth Engine assets.

These limitations should be considered when interpreting maps and using the results to support decisions.

## 12. Responsible Use of Results

The maps and projections are intended to support research, exploration, and planning discussions.

The 2031 projection should be treated as a scenario based on modelling assumptions rather than a guaranteed future outcome.

Decisions involving land acquisition, urban development, environmental regulation, or public investment should use additional evidence, appropriate validation, and relevant expert review.

## 13. Licence and Data Attribution

The original source code in this repository is intended to be released under the MIT License, subject to the terms of the included `LICENSE` file.

Third-party datasets, satellite imagery, administrative boundaries, and other external materials remain subject to their respective licences, attribution requirements, and terms of use.

The MIT License does not automatically apply to third-party data.

Refer to `DATA_SOURCES.md` for dataset-specific attribution and licensing information.

## 14. Author

**Akinyemi Akintola**  
Geospatial Data Science | Remote Sensing | Machine Learning

This project demonstrates the application of geospatial technologies and machine learning to land cover monitoring and future scenario analysis in Oyo State, Nigeria.

## 15. Acknowledgements

Acknowledgements are due to the organisations and communities that provide satellite observations, open geospatial datasets, analytical tools, and open-source software supporting environmental research.

Relevant data providers should be credited according to their specific attribution requirements.
**Project status:** Update this section to indicate whether the project is in development, undergoing validation, or completed.

**Last updated:** November 2026
