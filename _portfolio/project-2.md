---
title: "Mapping Poverty with Satellite Imagery and Machine Learning"
excerpt: "A CNN and transfer-learning framework using Landsat 8 daytime imagery to predict poverty rate, household income, and expenditure at the 1 km grid-cell level for Peru."
collection: portfolio
permalink: /portfolio/project-2
---

{% include base_path %}

## Description

This project uses daytime satellite imagery from Google Earth Engine (Landsat 8) to predict socioeconomic indicators -- poverty rate, household income, and expenditure -- at the 1 km² grid-cell level for Peru, following the transfer-learning-for-poverty-mapping approach (Yeh et al.). A CNN extracts visual features from daytime imagery (built-up density, roads, roofing materials, vegetation, etc.), which are combined with Census/survey socioeconomic features to train a regression model per target variable.

## Data Processing

Geospatial joins were performed between a 1 km grid-cell shapefile and socioeconomic variables from the 2017 Census, including educational attainment, age distribution, employment status, and poverty rate at the census-tract ("manzana"/block) level. Household income and expenditure from the ENAHO household survey (2014-2017) were added via a spatial join on household GPS coordinates. Both are aggregated up to the 1 km grid level. See `src/data/clean_economic_variables.py`.

Daytime imagery was sourced from Landsat 8 Collection 2 Level 2, filtered to remove cloud, cloud-shadow, and snow-contaminated pixels, and downloaded per grid cell via the Earth Engine API. Only grid cells in urban zones are downloaded, since the poverty-mapping model targets urban 1 km cells. See `src/data/landsat_download.ipynb`.

## CNN Pipeline

- `src/raster_utils.py` standardizes the downloaded grid tiles (which come out at slightly irregular pixel dimensions, since a 1 km cell rarely aligns to an exact integer number of Landsat pixels) to a fixed square size via bilinear resize, so every tile fed to the CNN has the same shape.
- `src/data/make_splits.py` assigns train/validation/test splits by spatially clustering grid cells within the same district (ubigeo), rather than splitting rows at random, so neighboring (highly correlated) cells don't leak between splits. Poverty and income/expenditure get independent splits, since they have different missing-data patterns.
- `src/features/prepare_data.py` joins the standardized images with the socioeconomic CSV (one target at a time: poverty, income, or expenditure), median-imputes and standardizes the features and target (fit only on the train split), and writes everything to TFRecords.
- `src/models/models.py` defines the CNN architecture: a stack of Conv2D + MaxPooling blocks over the image, optionally concatenated with the socioeconomic feature vector, feeding into dense layers and a single regression output.
- `src/models/train.py` runs a hyperparameter grid search (learning rate, L2, decay, filters, dropout) with TensorBoard logging and checkpointing, evaluating streaming R² (`src/utils.py`) on train/validation/test.
- `src/models/predict.py` scores a trained model, either on train/validation/test (`eval`, to report R² and true-vs-predicted values) or on another year's imagery with no ground truth (`predict`).

Each of the CNN pipeline steps above is run once per target variable (poverty, income, expenditure) -- a separate model is trained per variable, following the paper's design.

## Satellite Image Example

<figure>
  <img src="{{ base_path }}/images/day_time_lima.png" alt="Example of a daytime satellite image covering an urban area in Lima, Peru">
  <figcaption>
    Example of the daytime satellite imagery used in the project. The CNN learns visual features from the urban form, road network, vegetation, density, and surface textures to support small-area poverty, income, and expenditure prediction.
  </figcaption>
</figure>

## Project Repository

<a href="https://github.com/Robertopucp/CNN-PovertyRate-DayTimeImage" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on GitHub</a>
