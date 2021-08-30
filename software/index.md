---
layout: page
title: "Software"
modified: 2021-05-23
---

I am a core contributor and maintainer for many of the leading open source tools
for scientific computing in Python; see
[my GitHub profile](https://github.com/shoyer) for details.

Highlights:

- [Xarray](https://github.com/pydata/xarray) has become a standard tool
  for analyzing multi-dimensional datasets in Python (especially weather/climate
  data), and has contributed to [hundreds of scientific papers](https://scholar.google.com/scholar?oi=bibs&hl=en&cites=7605314348902559849,16897225769943537668,9041174076192873931,2969260840272984600).
  I created Xarray when I was a data scientist for The Climate Corporation,
  and now maintain it along with about a dozen other core developers. The project received hundreds of thousands of dollars in
  grant funding from the [Chan-Zuckerberg Initiative](https://chanzuckerberg.com/eoss/proposals/xarray-multidimensional-labeled-arrays-and-datasets-in-python/) and [NASA](https://medium.com/@numfocus/numfocus-projects-receive-nasa-grants-deee374e7a57), among others.
- [NumPy](https://github.com/numpy/numpy) is the fundamental package for
  scientific computing with Python, with
  [millions of users](https://bids.berkeley.edu/news/numpy-array-programming-core-scientific-python-ecosystem) in academia and
  industry. I'm on the NumPy steering council and wrote a number of
  [NEPs](https://numpy.org/neps/) focused on
  inter-operability between NumPy and other array libraries.
- [JAX](https://github.com/google/jax) is a Google project focused on machine
  learning research. I have made and reviewed many contributions to JAX, with a
  focus on scientific use-cases such as `jax.scipy`.

Other projects I created:

- [Xarray-Beam](https://github.com/google/xarray-beam) is a library for
  distributed computing with Xarray and Apache Beam.
- [h5netcdf](https://github.com/h5netcdf/h5netcdf) is an alternative
  implementation of the netCDF4 file-format in Python.
- [numbagg](https://github.com/shoyer/numbagg) is an experimental project that
  uses numba and NumPy universal functions to write fast N-dimensional array
  aggregation functions with very little boilerplate code.
- [cyordereddict](https://github.com/shoyer/cyordereddict) was a port of the
  Python standard library's `OrderedDict` to Cython. It ran 2-6x faster.

In the past, I was a core developer for [Dask](https://github.com/dask/dask)
and [Pandas](https://github.com/pandas-dev/pandas)
