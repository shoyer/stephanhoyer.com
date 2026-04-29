---
layout: page
title: Software
permalink: /software/
nav: true
nav_order: 2
---

I am a core contributor and maintainer of several widely used tools for
scientific computing in Python. See
[my GitHub profile](https://github.com/shoyer) for the full list.

This page covers the general-purpose libraries. Many of my research projects
also have their own open source releases — including
[NeuralGCM](https://github.com/neuralgcm/neuralgcm),
[JAX-CFD](https://github.com/google/jax-cfd),
[Dinosaur](https://github.com/neuralgcm/dinosaur) and others. See
[Research](/research/) for the full picture.

## Xarray — primary author

[Xarray](https://xarray.dev) is a library for multi-dimensional labeled data
in Python that has been widely adopted across weather and climate, geospatial
analysis, plasma physics, genomics, and finance. The project is
[downloaded **~5m times per week**](https://pypistats.org/packages/xarray),
with **4,000+ stars** and **500+ contributors** on GitHub.

I created Xarray in 2014 while at The Climate Corporation and continue to
lead the project, working with a team of 21 volunteer and grant-funded
developers. Xarray has received over $500,000 in grant funding from the NSF,
NASA, Nvidia and the [Chan-Zuckerberg Initiative](https://chanzuckerberg.com/eoss/proposals/xarray-multidimensional-labeled-arrays-and-datasets-in-python/).

## Xarray-Beam — primary author

[Xarray-Beam](https://github.com/google/xarray-beam) implements reliable
large-scale data pipelines on Xarray data using the map-reduce paradigm
(via Apache Beam). Six weather research teams at Google use it to process
petabytes of data.

## NumPy — former steering council member

I served on the [NumPy](https://numpy.org) steering council from 2015 and
authored six [NumPy Enhancement Proposals](https://numpy.org/neps/), focused
on interoperability between NumPy and other array libraries. Contributions
include widely used functionality such as `broadcast_to`, `stack`, `moveaxis`
and `__array_function__`.

## JAX — committer

I have contributed [100+ pull requests](https://github.com/jax-ml/jax/pulls?q=is%3Apr+author%3Ashoyer)
to [JAX](https://github.com/jax-ml/jax), focused on matrix-free linear algebra
and scientific computing — including much of `jax.scipy`.

## Other projects

- [h5netcdf](https://github.com/h5netcdf/h5netcdf) — an alternative
  implementation of the netCDF4 file format in Python.
- [numbagg](https://github.com/shoyer/numbagg) — fast N-dimensional
  aggregation functions built with Numba and NumPy ufuncs.
- [cyordereddict](https://github.com/shoyer/cyordereddict) — a Cython port of
  the Python standard library's `OrderedDict`, 2–6× faster.

In the past I was also a core developer for
[Dask](https://github.com/dask/dask) and
[Pandas](https://github.com/pandas-dev/pandas).
