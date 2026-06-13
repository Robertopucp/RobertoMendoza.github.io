---
title: "Hurricanes and Real Estate Values: Interactive Power BI Dashboard"
excerpt: "An interactive Power BI dashboard integrating Zillow and FEMA data to explore how major hurricanes relate to county-level housing values in the United States."
collection: portfolio
permalink: /portfolio/project-4
---

{% include base_path %}

## Overview

I developed this interactive dashboard for an Environmental Economics course to examine how major hurricanes affect county-level real estate values in the United States. The project provides an accessible way to explore housing-market trends before and after hurricane events across affected locations.

## Data Integration

The dashboard combines two primary data sources:

- **Zillow Home Value Index (ZHVI):** County-level time-series estimates of typical residential property values.
- **FEMA hurricane records:** Information on major hurricane events and affected geographic areas.

The datasets were cleaned, transformed, and linked geographically to support interactive comparisons of housing values across counties and hurricane periods.

## Dashboard Features

- An interactive U.S. map for direct county selection
- State and county dropdown filters
- County-level ZHVI trends over time
- Summary indicators comparing average home values during post-hurricane and no-hurricane periods
- Shaded post-hurricane periods in the time-series chart
- Interactive labels identifying the hurricanes associated with each affected period

## Dashboard Preview

<figure>
  <img src="{{ base_path }}/images/dashboard.png" alt="Interactive Power BI dashboard showing hurricane events and county-level Zillow Home Value Index trends in the United States">
  <figcaption>
    Power BI dashboard integrating county-level Zillow Home Value Index data with FEMA hurricane records. Users can select locations from the map or filters and inspect housing-value trends around major hurricane events.
  </figcaption>
</figure>