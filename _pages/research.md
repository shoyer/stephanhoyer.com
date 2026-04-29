---
layout: page
title: Research
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
Agriculture.

On the technical side, I personally implemented many of the key components,
including model and data parallelism scaling to 256 TPUs.

- [Neural general circulation models for weather and climate](https://www.nature.com/articles/s41586-024-07744-y).
  D Kochkov, J Yuval, …, **S Hoyer**. *Nature* (2024).
- [WeatherBench 2: A benchmark for the next generation of data-driven global weather models](https://arxiv.org/abs/2308.15560).
  S Rasp, **S Hoyer**, et al. *Journal of Advances in Modeling Earth Systems* (2024).
- [Learning skillful medium-range global weather forecasting](https://www.science.org/doi/10.1126/science.adi2336).
  R Lam et al. *Science* (2023).

## AI for fluids

For several years I led a research program on accelerating fluid simulations
using deep learning and Google TPUs. The program produced six peer-reviewed
publications (two in *PNAS*) and over 2,000 citations.

- [Machine learning–accelerated computational fluid dynamics](https://www.pnas.org/doi/10.1073/pnas.2101784118).
  D Kochkov, …, **S Hoyer**. *PNAS* (2021).
- [Learning data-driven discretizations for partial differential equations](https://www.pnas.org/doi/10.1073/pnas.1814058116).
  Y Bar-Sinai\*, **S Hoyer**\*, J Hickey, MP Brenner. *PNAS* (2019).
- [Variational data assimilation with a learned inverse observation operator](https://arxiv.org/abs/2102.11192).
  *ICML* (2021).

## AI for physics

I have published research applying machine learning to a range of problems
across the physical sciences, including drug discovery, microscopy,
nanophotonics, quantum chemistry, structural engineering, flood modeling and
fundamental physics.

- [Lagrangian neural networks](https://arxiv.org/abs/2003.04630).
  M Cranmer, S Greydanus, **S Hoyer**, et al. *arXiv* (2020).
- [Kohn–Sham equations as regularizer: building prior knowledge into machine-learned physics](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.126.036401).
  L Li, **S Hoyer**, et al. *Physical Review Letters* (2021).
- [Free-form diffractive metagrating design based on generative adversarial networks](https://pubs.acs.org/doi/10.1021/acsnano.9b02371).
  J Jiang, D Sell, **S Hoyer**, J Hickey, J Yang, JA Fan. *ACS Nano* (2019).
- [Neural reparameterization improves structural optimization](https://arxiv.org/abs/1909.04240).
  **S Hoyer**, et al. *NeurIPS workshop* (2019).

## Fundamental AI research

At Google, I collaborated with researchers at DeepMind and Google Brain and
published in top machine learning conferences.

- [Efficient and modular implicit differentiation](https://arxiv.org/abs/2105.15183).
  M Blondel et al. *NeurIPS* (2022).
- [The Cramér distance as a solution to biased Wasserstein gradients](https://arxiv.org/abs/1705.10743).
  M Bellemare et al. *arXiv* (2017).

## Tools for scientific computing at scale

Alongside specific research projects, I have contributed to general-purpose
tools for working with large scientific datasets, including
[Xarray](https://xarray.dev), [NumPy](https://numpy.org) and
[JAX](https://github.com/jax-ml/jax). See [Software](/software/) for the
open source projects.

- [Array programming with NumPy](https://www.nature.com/articles/s41586-020-2649-2).
  CR Harris et al. *Nature* (2020).
- [Xarray: N-D labeled arrays and datasets in Python](https://openresearchsoftware.metajnl.com/articles/10.5334/jors.148).
  **S Hoyer**, J Hamman. *Journal of Open Research Software* (2017).

## Earlier: quantum dynamics

Before joining industry I completed a Ph.D. in theoretical physics at UC
Berkeley with [Birgitta Whaley](http://www.cchem.berkeley.edu/kbwgrp/),
working on
[quantum dynamics in photosynthetic light harvesting](http://www2.lbl.gov/Science-Articles/Archive/PBD-quantum-secrets.html)
(2008–2013).

- [Limits of quantum speedup in photosynthetic light harvesting](https://arxiv.org/abs/0910.1847).
  **S Hoyer**, M Sarovar, KB Whaley. *New Journal of Physics* (2010).
- [Faster transport with a directed quantum walk](https://arxiv.org/abs/0901.1007).
  **S Hoyer**, DA Meyer. *Physical Review A* (2009).
