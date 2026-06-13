---
title: "Mapping Poverty with Satellite Imagery and Machine Learning"
excerpt: "Work in progress: a CNN and Ridge regression framework for predicting poverty rates and household income across populated 1 km grid cells."
collection: portfolio
permalink: /portfolio/project-3
---

{% include base_path %}

**Project status:** Work in progress

## Overview

This project develops a deep and machine learning framework to estimate poverty rates and household income at a fine spatial resolution. The objective is to complement conventional survey data with daytime satellite imagery and socioeconomic information, producing estimates across populated **1 km grid cells**.

## Current Progress

The end-to-end **ETL and data processing pipeline is complete**. It prepares satellite imagery, socioeconomic variables, population data, and poverty outcomes at a consistent grid-cell level.

The completed workflow includes:

- Acquisition and preprocessing of daytime satellite images
- Construction of populated 1 km grid cells
- Spatial alignment of imagery and socioeconomic data
- Data cleaning, transformation, and feature preparation
- Creation of model-ready training and validation datasets

## Planned Machine Learning Framework

The next phase will implement a **Convolutional Neural Network (CNN)** to learn visual representations from satellite images. The CNN will extract features related to edges, shapes, textures, settlement density, road patterns, vegetation, and other characteristics of the built environment.

The learned image features will be combined with socioeconomic variables at the grid-cell level. An **L2-regularized linear model (Ridge regression)** will then use the combined feature set to predict:

- Poverty rates
- Household income

Regularization will help control model complexity when working with a large set of correlated image and socioeconomic features.

## Satellite Image Example

<figure>
  <img src="{{ base_path }}/images/day_time_lima.png" alt="Example of a daytime satellite image covering an urban area in Lima, Peru">
  <figcaption>
    Example of the daytime satellite imagery used in the project. The CNN will learn visual features from the urban form, road network, vegetation, density, and surface textures to support small-area poverty and income prediction.
  </figcaption>
</figure>

