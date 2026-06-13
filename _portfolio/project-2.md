---
title: "Migratory regularisation and Local Economic Activity in Colombia"
excerpt: "Local economic effects of large-scale Venezuelan regularisation into Colombia."
collection: portfolio
permalink: /portfolio/project-2
---

{% include base_path %}

## Overview

This project examines the local economic effects of the large-scale Venezuelan regularisation wave into Colombia. Because conventional economic statistics may be unavailable at high spatial and temporal resolutions, I use non-conventional proxies derived from remote sensing data to measure changes in economic activity and land use.

The main outcomes include **Night Light Density (NLD)**, urban expansion, cropland cover, and CO2 emissions. Together, these measures provide complementary evidence on local economic activity, development patterns, and environmental change.

## Data Engineering and Remote Sensing

I developed an end-to-end geospatial data pipeline using **Python** and **Google Earth Engine**. The workflow retrieves, processes, harmonizes, and aggregates satellite-based indicators at the geographic level required for the empirical analysis.

## Event Study

I use an event-study design to trace changes in local economic activity before and after the policy-related treatment period. The specification makes it possible to inspect pre-treatment dynamics and evaluate how the estimated effect evolves over time.

<figure>
  <img src="{{ base_path }}/images/Event_study.png" alt="Event-study estimates of the effect of Venezuelan migration on Night Light Density in Colombia">
  <figcaption>
    Event-study estimates for Night Light Density. The vertical red line marks the treatment period in 2018. Estimates become positive from 2019 onward, indicating an increase in satellite-observed economic activity after treatment. Points represent annual estimates and error bars show their uncertainty.
  </figcaption>
</figure>

## Main Finding

The post-treatment estimates indicate an increase in Night Light Density in areas affected by the migration-related policy. This pattern is consistent with an expansion in local economic activity, as captured by nighttime satellite imagery.


