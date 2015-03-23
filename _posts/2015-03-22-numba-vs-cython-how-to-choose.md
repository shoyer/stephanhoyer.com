---
layout: post
title: "Numba vs Cython: How to Choose"
excerpt: "The non-performance trade-offs between using Numba and Cython for
accelerating scientific Python code"
modified:
categories:
date: 2015-03-22T17:00:00-07:00
draft: true
---

Recently, [Dale Jung](http://dalejung.com) asked me about my heuristics for
choosing between [Numba](http://numba.pydata.org/) and
[Cython](http://cython.org/) for accelerating scientific Python code. Following
the general principle that it's a better idea to write blog post than an email
to one person, here's an extended version of my reply.

<hr />

Numba and Cython are two tools I can recommend for accelerating scientific
Python code. There are plenty of examples out there comparing performance for
Cython, Numba and other options (I like
[this post](https://jakevdp.github.io/blog/2013/06/15/numba-vs-cython-take-2/)
by Jake VanderPlas), but these don't make the choice easy. Both can produce
highly performant code that looks a lot like normal Python, and the speed
differences aren't large or general enough to make either a clear winner.

Here are my thoughts, broken down by some guiding questions.

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
(especially if you use Conda), then Numba can be a great choice.

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
features and then only tweaks the bottlenecks for speed can be really nice.

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
a [`vectorize`](http://numba.pydata.org/numba-doc/0.17.0/user/vectorize.html)
decorator. In other cases, Numba can handle arbitrary dimensional input by
using Just-In-Time compilation with `jit` or by creating generalized universal
functions with `guvectorize`.

In contrast, generally speaking, your Cython functions will only work for input
with a number of dimensions that you determine ahead of time (e.g., a 1D
vector, but not a scalar or 2D array).
It certainly possible to do this sort of stuff with Cython, but it's not
easy, and you'll need to get your hands dirty with the
[NumPy C-API](http://docs.scipy.org/doc/numpy/reference/c-api.html).
Keith Goodman has some nice examples in [version 1.0 of bottleneck](https://github.com/kwgoodman/bottleneck/issues/92).

## Still not sure?

Give Numba a try. Numba is usually easier to write for the simple cases where
it works. You may still run into annoying limitations when you try to do
complex things but Numba has been getting a lot better, even just over the past
few months (e.g., they recently added support for
[generating random numbers](https://github.com/numba/numba/pull/981)).
The Numba devs have also been highly responsive to the issues I've encountered
writing [numbagg](https://github.com/shoyer/numbagg). At the end of the day,
even if you ultimately can't get things to work to work, you'll still have
idiomatic Python code that should be easy to accelerate with Cython.
