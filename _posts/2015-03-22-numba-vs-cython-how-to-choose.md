---
layout: post
title: "Numba vs Cython: How to Choose"
excerpt: "The non-performance trade-offs between using Numba and Cython for
accelerating scientific Python code"
modified:
categories:
date: 2015-03-22T17:00:00-07:00
draft: true
comments: true
---

Recently, [Dale Jung](http://dalejung.com) asked me about my heuristics for
choosing between [Numba](http://numba.pydata.org/) and
[Cython](http://cython.org/) for accelerating scientific Python code. Following
the general principle that it's a better idea to write blog post than an email
to one person, here's an extended version of my reply.

<hr />

Most of the time, libraries like [NumPy](http://numpy.org),
[SciPy](http://scipy.org) and [pandas](http://pandas.pydata.org), whose
critical loops are already written in a compiled language like C, are enough
fast scientific Python code.

Unfortunately, sometimes you need to write your own loop in performance
critical paths of your code, and unfortunately loops in Python are painfully
slow. This is where Numba and Cython come in: they both promise the ability to
write the inner loop of your code in something that looks a lot like normal
Python, but that runs about as fast as handwritten C.

Numba uses LLVM to power Just-In-Time compilation of array oriented Python
code. Using Numba is usually about as simple as adding a decorator to your
functions:
{% highlight python %}
from numba import jit

@jit
def numba_mean(x):
    total = 0
    for xi in x:
        total += xi
    return total / len(x)
{% endhighlight %}
You can supply optional types, but they aren't required for performant code,
as Numba can compile functions on the fly using its JIT compiler.

In contrast, Cython is a general purpose tool (not just for array
oriented computing) that compiles Python into C extensions. To see impressive
speedups, you need to manually add types:
{% highlight cython %}
def cython_mean(double[:] x):
    cdef double total = 0
    for i in range(len(x)):
        total += x[i]
    return total / len(x)
{% endhighlight %}

When I benchmark this example, IPython's `%timeit` reports that calling this
function on a 100000 element array takes on average ~93 µs with Numba and ~96
µs with Cython. The undecorated function in pure Python is 17x slower.
(`numpy.mean` is faster than either Cython or Numba, at ~60 µs, but here we're
pretending that we needed to write our own custom function that was not already
built in. And frankly, 50% slower than C is probably still fast enough.)

This trivial example illustrates my broader experience with Numba and Cython:
both are pretty easy to use, and result in roughly equivalently fast code.
For similar results on a less contrived example, see
[this blog post](https://jakevdp.github.io/blog/2013/06/15/numba-vs-cython-take-2/)
by Jake VanderPlas.

The bottom line is that even though performance is why we reach for tools like
Numba and Cython, performance does not provide a good basis for choosing one
over the other. Here are the questions I asked myself when making that choice
for my projects.

## Is this code for one-off use or a library?

Cython is easier to distribute than Numba, which makes it a better option for
user facing libraries. It's the preferred option for most of the scientific
Python stack, including NumPy, SciPy, pandas and Scikit-Learn. In contrast,
there are very few libraries that use Numba. I know of two, both of which are
basically in the experimental phase:
[Blaze](https://github.com/continuumio/blaze) and my project
[numbagg](https://github.com/shoyer/numbagg).

The main issue is that it can be difficult to install Numba unless you use
[Conda](http://conda.pydata.org/) (which I highly recommend). In contrast,
distributing a package with Cython based C-extensions is almost miraculous
easy. Cython is also a more stable and mature platform, whereas the features
and performance of Numba are still evolving.

If you don't need to distribute your code beyond your computer or your team
(especially if you use Conda), then Numba can be a great choice. Otherwise, you
should lean toward Cython.

## Do you need advanced Python features or to use C-level APIs?

The features that Numba supports in the accelerated `nopython` mode are very
limited. For example:

- Numba only accelerates code that uses scalars or (N-dimensional) arrays. You
  can't use built-in types like `list` or `dict` or your own custom classes.
- You can't [allocate new arrays](https://github.com/numba/numba/pull/719) in
  accelerated code.
- You can't use [recursion](https://github.com/numba/numba/pull/719).

Some of these are [design decisions](http://numba.pydata.org/numba-doc/0.17.0/user/troubleshoot.html); in other cases, these are being actively worked on.

In contrast, Cython can compile arbitrary Python code, and can even directly
call C. The ability to Cythonize an entire module written using advanced Python
features and then only tweak the bottlenecks for speed can be really nice.

For example, switching to an
[extension type](http://docs.cython.org/src/userguide/extension_types.html) and
calling C APIs directly can make for big differences in speed, even if you
still rely on builtin Python types like lists or dictionaries. Writing
something like [cyordereddict](https://github.com/shoyer/cyordereddict) in
Numba would be nearly impossible.

## Do you want to write code that works on N-dimensional arrays?

Suppose you want a function that takes several arguments and returns a scalar
or array, depending on the number of provided arguments. For example,
consider a function that averages two numbers:

{% highlight python %}
def average(a, b):
    return 0.5 * (a + b)
{% endhighlight %}

One of the most powerful features of NumPy is that this simple function would
work even if `a` or `b` are multi-dimensional arrays (tensors), by following
[broadcasting rules](http://docs.scipy.org/doc/numpy/user/basics.broadcasting.html).

Numba makes it easy to accelerate functions with broadcasting by simply adding
the [`vectorize`](http://numba.pydata.org/numba-doc/0.17.0/user/vectorize.html)
decorator. This produces universal functions (ufuncs) that automatically work
(even preserving labels) on array-like data structures in the entire scientific
Python ecosystem, including [xray](http://xray.readthedocs.org) and
[pandas](http://pandas.pydata.org). In other cases, Numba can handle arbitrary
dimensional input by using Just-In-Time compilation with `jit` or by creating
generalized universal functions with `guvectorize`.

In contrast, generally speaking, your Cython functions will only work for input
with a number of dimensions that you determine ahead of time (e.g., a 1D
vector, but not a scalar or 2D array).
It certainly possible to do this sort of stuff with Cython, but it's not
easy, and you'll need to get your hands dirty with the
[NumPy C-API](http://docs.scipy.org/doc/numpy/reference/c-api.html).
Keith Goodman has some nice examples in [version 1.0 of bottleneck](https://github.com/kwgoodman/bottleneck/issues/92).

## Still not sure?

When I'm not constrained by other concerns, I'll try to make Numba work. Numba
is usually easier to write for the simple cases where it works. You may still
run into annoying limitations when you try to do complex things, but Numba has
been getting a lot better, even just over the past few months (e.g., they
recently added support for
[generating random numbers](https://github.com/numba/numba/pull/981)).
At the end of the day, even if you ultimately can't get things to work, you'll
still have idiomatic Python code that should be easy to accelerate with Cython.
