---
title: "Mining Expansion: Machine Learning and Heterogeneous Treatment Effects"
excerpt: "A machine learning and causal inference framework for estimating exposure to mine expansion and uncovering heterogeneous treatment effects across households."
collection: portfolio
permalink: /portfolio/project-1
---

{% include base_path %}

## Overview

This project combines machine learning and causal inference to study the socioeconomic effects of mine expansion. I estimate each district's probability of being affected by the expansion using pre-treatment characteristics and then apply a causal forest to examine how treatment effects vary across households.

## Treatment Assignment Model

I train machine learning classifiers to predict the probability that a district is affected by mine expansion. Predictors include distance to the mine, the share of skilled workers, access to basic services, poverty rates, public expenditure, and other pre-treatment socioeconomic characteristics.

Four classifiers are evaluated:

- Kernel logistic regression with an RBF kernel
- Random forest
- Decision tree
- Gradient boosting

I use nested cross-validation to prevent information leakage between hyperparameter tuning and model evaluation. The best-performing classifier is selected using the outer cross-validation log-loss. The resulting propensity scores are trimmed to the region of common support so that treated and control districts have comparable pre-treatment characteristics.

## Heterogeneous Treatment Effects

I then estimate heterogeneous treatment effects using a causal forest. This flexible, data-driven method captures nonlinearities and interactions without requiring the sources of heterogeneity to be specified in advance. It also helps identify which household characteristics are most predictive of variation in the estimated treatment effect.

## Treatment Effect by Age

<figure>
  <img src="{{ base_path }}/images/HTE_effect.png" alt="Estimated heterogeneous treatment effect of mine expansion by age of the household head">
  <figcaption>
    Estimated treatment effects by age of the household head. The model indicates that the treatment effect is positive but generally decreases with age.
  </figcaption>
</figure>

## Technical Highlights

- Machine learning classification and hyperparameter tuning
- Nested cross-validation and log-loss evaluation
- Propensity-score estimation and common-support trimming
- Causal forests and heterogeneous treatment-effect estimation
- Data-driven analysis of treatment-effect moderators
