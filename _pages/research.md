---
layout: page
title: research
permalink: /research/
nav: true
nav_order: 1
---

I work on deep learning for the physical sciences, with a particular focus on
weather and climate modeling and on accelerating scientific simulations. My
collaborators and I have published in *Nature*, *Science*, *PNAS*, *Physical
Review Letters* and *NeurIPS*.

For a complete list, see my
[Google Scholar profile](https://scholar.google.com/citations?user=bWTG5FgAAAAJ)
(40,000+ citations, h-index 29).

## AI for weather and climate

I conceived and led the
[Neural General Circulation Models](https://github.com/neuralgcm/neuralgcm)
project at Google Research. NeuralGCM is the first AI-based model to improve
on traditional physics-based 15-day weather forecasts and atmosphere-only
climate simulations. It combines a differentiable atmospheric dynamical core
written in JAX with learned parameterizations for sub-grid physics, and is
trained end-to-end on reanalysis data.

The work was published in *Nature* (2024) with 16 co-authors, and received
press coverage in
[Bloomberg](https://www.bloomberg.com/news/articles/2024-07-22/google-develops-highly-accurate-ai-enhanced-weather-simulator)
and
[MIT Technology Review](https://www.technologyreview.com/2024/07/22/1095184/a-new-weather-prediction-model-from-google-combines-ai-with-traditional-physics/),
among others. The open-source model has since been used to produce
state-of-the-art
[monsoon-onset forecasts sent to 38 million farmers in India](https://blog.google/technology/research/indian-farmers-monsoon-prediction/),
in collaboration with the University of Chicago and the Indian Ministry of
Agriculture. A follow-on paper extended NeuralGCM to predict precipitation
directly from satellite observations, substantially improving on existing
GCMs and a global cloud-resolving model — particularly for the most intense
rainfall events. We are currently finalizing a $5M grant to a non-profit
partner to develop NeuralGCM into a full coupled climate model.

On the technical side, I personally implemented many of the key components,
including model and data parallelism scaling to 256 TPUs.

I also contributed to [WeatherBench 2](https://github.com/google-research/weatherbench2),
the standard open benchmark for the next generation of data-driven global
weather models.

Selected publications:

- **Neural general circulation models for weather and climate.**
  D Kochkov, J Yuval, …, **S Hoyer**. *Nature* (2024).
- **WeatherBench 2: A benchmark for the next generation of data-driven
  global weather models.**
  S Rasp, **S Hoyer**, et al. *Journal of Advances in Modeling Earth Systems*
  (2024).
- **Learning skillful medium-range global weather forecasting.**
  R Lam et al. *Science* (2023).

## AI for fluids

For several years I led a research program on accelerating fluid simulations
using deep learning and Google TPUs. The program produced six peer-reviewed
publications (two in *PNAS*) and over 2,000 citations.

- **Machine learning–accelerated computational fluid dynamics.**
  D Kochkov, …, **S Hoyer**. *PNAS* (2021).
- **Learning data-driven discretizations for partial differential equations.**
  Y Bar-Sinai\*, **S Hoyer**\*, J Hickey, MP Brenner. *PNAS* (2019).
- **Variational data assimilation with a learned inverse observation operator.**
  *ICML* (2021).

## AI for physics

I have published research applying machine learning to a range of problems
across the physical sciences, including drug discovery, microscopy,
nanophotonics, quantum chemistry, structural engineering, flood modeling and
fundamental physics.

- **Lagrangian neural networks.**
  M Cranmer, S Greydanus, **S Hoyer**, et al. *arXiv* (2020).
- **Kohn–Sham equations as regularizer: building prior knowledge into
  machine-learned physics.**
  L Li, **S Hoyer**, et al. *Physical Review Letters* (2021).
- **Free-form diffractive metagrating design based on generative adversarial
  networks.**
  J Jiang, D Sell, **S Hoyer**, J Hickey, J Yang, JA Fan. *ACS Nano* (2019).
- **Neural reparameterization improves structural optimization.**
  **S Hoyer**, et al. *NeurIPS workshop* (2019).

## Fundamental AI research

- **Efficient and modular implicit differentiation.**
  M Blondel et al. *NeurIPS* (2022).
- **The Cramér distance as a solution to biased Wasserstein gradients.**
  M Bellemare et al. *arXiv* (2017).

## Tools for scientific computing at scale

While at Google I built tools for high-performance data pipelines —
training, inference and analytics — that process petabytes of weather data
in Zarr format, used by all Google weather teams. I have made 100+
contributions to JAX and TensorFlow. See [Software](/software/) for the
open source projects.

## Earlier: quantum dynamics

Before joining industry I completed a Ph.D. in theoretical physics at UC
Berkeley with [Birgitta Whaley](http://www.cchem.berkeley.edu/kbwgrp/),
working on
[quantum dynamics in photosynthetic light harvesting](http://www2.lbl.gov/Science-Articles/Archive/PBD-quantum-secrets.html)
(2008–2013).
