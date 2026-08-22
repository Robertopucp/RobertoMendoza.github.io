---
title: "The Effect of El Niño 2017 on Firm Productivity"
excerpt: "Master's thesis research applying causal inference and machine learning to measure how a large-scale climate shock affected firm-level productivity in Peru."
collection: portfolio
permalink: /portfolio/project-5
---

{% include base_path %}

## Overview

Master's thesis research applying causal inference and machine learning to measure how a large-scale climate shock affected firm-level productivity in Peru. The project combines panel econometrics, supervised and unsupervised machine learning, and satellite remote sensing data.

## Abstract

Latin America's productivity growth has been historically low and stagnant. In Peru, the average TFP growth rate has been barely 0.1% over the last decade, raising concerns about the shocks that shape productivity. This thesis examines whether El Niño 2017, which brought intense rainfall and flooding to the Peruvian coast and severe drought to the southern Andes, reduced firm-level total factor productivity (TFP).

Using firm panel data from 2012 to 2020 and geographic variation in precipitation anomalies, I estimate a two-way fixed-effects difference-in-differences model comparing firms in flood-prone districts (rainfall anomaly ≥ 60mm) to firms in districts with a mild or weak anomaly (0-30mm). El Niño 2017 reduced TFP by 12.1% to 13.6%, significant at the 1% level and robust to alternative productivity measures and machine-learning-based estimators. The short-run effect is concentrated in small firms and the commerce and services sectors, driven by a demand contraction and worse employee health, while manufacturing exhibits a persistent decline through 2019 due to infrastructure recovery. Affected firms also cut training expenditure and the share of college-educated employees. In the long run, El Niño 1998 is associated with lower firm-level labor productivity.

I also leverage remote sensing data, using nighttime light density at the district level as a proxy for economic activity, to examine the long-run effects of El Niño.

## Key Techniques

- **Causal inference:** Double/Debiased Machine Learning
- **Machine learning:** K-Means and hierarchical clustering, Support Vector Machines, Random Forest, Gradient Boosting, XGBoost, Lasso-based variable selection
- **Model validation:** Nested cross-validation (grid search for hyperparameter tuning, held-out folds for performance evaluation)
- **Geospatial analysis:** Shapefile processing, spatial joins, distance-to-boundary calculations, satellite nighttime-lights extraction via Google Earth Engine

## Project Repository

<a href="https://github.com/Robertopucp/MasterProgram_Research" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on GitHub</a>
