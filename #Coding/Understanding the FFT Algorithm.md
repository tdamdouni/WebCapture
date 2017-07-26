# Understanding the FFT Algorithm

_Captured: 2016-10-31 at 22:44 from [jakevdp.github.io](http://jakevdp.github.io/blog/2013/08/28/understanding-the-fft/)_

Aug 28, 2013

The Fast Fourier Transform (FFT) is one of the most important algorithms in
signal processing and data analysis. I've used it for years, but having no
formal computer science background, It occurred to me this week that I've
never thought to ask _how_ the FFT computes the discrete Fourier transform so
quickly. I dusted off an old algorithms book and looked into it, and enjoyed
reading about the deceptively simple computational trick that JW Cooley and
John Tukey outlined in their classic [1965 paper](http://www.ams.org/journals/
mcom/1965-19-090/S0025-5718-1965-0178586-1/) introducing the subject.

The goal of this post is to dive into the Cooley-Tukey FFT algorithm,
explaining the symmetries that lead to it, and to show some straightforward
Python implementations putting the theory into practice. My hope is that this
exploration will give data scientists like myself a more complete picture of
what's going on in the background of the algorithms we use.

## The Discrete Fourier Transform¶

The FFT is a fast, \\(\mathcal{O}[N\log N]\\) algorithm to compute the
Discrete Fourier Transform (DFT), which naively is an \\(\mathcal{O}[N^2]\\)
computation. The DFT, like the more familiar continuous version of the Fourier
transform, has a forward and inverse form which are defined as follows:

**Forward Discrete Fourier Transform (DFT):** \\[X_k = \sum_{n=0}^{N-1} x_n \cdot e^{-i~2\pi~k~n~/~N}\\]

**Inverse Discrete Fourier Transform (IDFT):** \\[x_n = \frac{1}{N}\sum_{k=0}^{N-1} X_k e^{i~2\pi~k~n~/~N}\\]

The transformation from \\(x_n \to X_k\\) is a translation from configuration
space to frequency space, and can be very useful in both exploring the power
spectrum of a signal, and also for transforming certain problems for more
efficient computation. For some examples of this in action, you can check out
Chapter 10 of our upcoming Astronomy/Statistics book, with figures and Python
source code available [here](http://www.astroml.org/book_figures/chapter10/).
For an example of the FFT being used to simplify an otherwise difficult
differential equation integration, see my post on [Solving the Schrodinger
Equation in Python](http://jakevdp.github.io/blog/2012/09/05/quantum-python/).

Because of the importance of the FFT in so many fields, Python contains many
standard tools and wrappers to compute this. Both NumPy and SciPy have
wrappers of the extremely well-tested FFTPACK library, found in the submodules
`numpy.fft` and `scipy.fftpack` respectively. The fastest FFT I am aware of is
in the [FFTW](http://www.fftw.org/) package, which is also available in Python
via the [PyFFTW](https://pypi.python.org/pypi/pyFFTW) package.

For the moment, though, let's leave these implementations aside and ask how we
might compute the FFT in Python from scratch.

## Computing the Discrete Fourier Transform¶

For simplicity, we'll concern ourself only with the forward transform, as the
inverse transform can be implemented in a very similar manner. Taking a look
at the DFT expression above, we see that it is nothing more than a
straightforward linear operation: a matrix-vector multiplication of
\\(\vec{x}\\),

\\[\vec{X} = M \cdot \vec{x}\\]

with the matrix \\(M\\) given by

\\[M_{kn} = e^{-i~2\pi~k~n~/~N}.\\]

With this in mind, we can compute the DFT using simple matrix multiplication
as follows:

In [1]:

    
    
    import numpy as np
    def DFT_slow(x):
        """Compute the discrete Fourier Transform of the 1D array x"""
        x = np.asarray(x, dtype=float)
        N = x.shape[0]
        n = np.arange(N)
        k = n.reshape((N, 1))
        M = np.exp(-2j * np.pi * k * n / N)
        return np.dot(M, x)
    

We can double-check the result by comparing to numpy's built-in FFT function:

In [2]:

    
    
    x = np.random.random(1024)
    np.allclose(DFT_slow(x), np.fft.fft(x))
    

Out[2]:

    
    
    True
    

Just to confirm the sluggishness of our algorithm, we can compare the
execution times of these two approaches:

In [3]:

    
    
    %timeit DFT_slow(x)
    %timeit np.fft.fft(x)
    
    
    
    10 loops, best of 3: 75.4 ms per loop
    10000 loops, best of 3: 25.5 µs per loop
    
    

We are over 1000 times slower, which is to be expected for such a simplistic
implementation. But that's not the worst of it. For an input vector of length
\\(N\\), the FFT algorithm scales as \\(\mathcal{O}[N\log N]\\), while our
slow algorithm scales as \\(\mathcal{O}[N^2]\\). That means that for
\\(N=10^6\\) elements, we'd expect the FFT to complete in somewhere around 50
ms, while our slow algorithm would take nearly 20 hours!

So how does the FFT accomplish this speedup? The answer lies in exploiting
symmetry.

## Symmetries in the Discrete Fourier Transform¶

One of the most important tools in the belt of an algorithm-builder is to
exploit symmetries of a problem. If you can show analytically that one piece
of a problem is simply related to another, you can compute the subresult only
once and save that computational cost. Cooley and Tukey used exactly this
approach in deriving the FFT.

We'll start by asking what the value of \\(X_{N+k}\\) is. From our above
expression:

\\[ \begin{align*} X_{N + k} &= \sum_{n=0}^{N-1} x_n \cdot e^{-i~2\pi~(N +
k)~n~/~N}\\\ &= \sum_{n=0}^{N-1} x_n \cdot e^{- i~2\pi~n} \cdot
e^{-i~2\pi~k~n~/~N}\\\ &= \sum_{n=0}^{N-1} x_n \cdot e^{-i~2\pi~k~n~/~N}
\end{align*} \\]

where we've used the identity \\(\exp[2\pi~i~n] = 1\\) which holds for any
integer \\(n\\).

The last line shows a nice symmetry property of the DFT:

\\[X_{N+k} = X_k.\\]

By a simple extension,

\\[X_{k + i \cdot N} = X_k\\]

for any integer \\(i\\). As we'll see below, this symmetry can be exploited to
compute the DFT much more quickly.

## DFT to FFT: Exploiting Symmetry¶

Cooley and Tukey showed that it's possible to divide the DFT computation into
two smaller parts. From the definition of the DFT we have:

\\[ \begin{align} X_k &= \sum_{n=0}^{N-1} x_n \cdot e^{-i~2\pi~k~n~/~N} \\\ &=
\sum_{m=0}^{N/2 - 1} x_{2m} \cdot e^{-i~2\pi~k~(2m)~/~N} + \sum_{m=0}^{N/2 -
1} x_{2m + 1} \cdot e^{-i~2\pi~k~(2m + 1)~/~N} \\\ &= \sum_{m=0}^{N/2 - 1}
x_{2m} \cdot e^{-i~2\pi~k~m~/~(N/2)} + e^{-i~2\pi~k~/~N} \sum_{m=0}^{N/2 - 1}
x_{2m + 1} \cdot e^{-i~2\pi~k~m~/~(N/2)} \end{align} \\]

We've split the single Discrete Fourier transform into two terms which
themselves look very similar to smaller Discrete Fourier Transforms, one on
the odd-numbered values, and one on the even-numbered values. So far, however,
we haven't saved any computational cycles. Each term consists of \\((N/2)*N\\)
computations, for a total of \\(N^2\\).

The trick comes in making use of symmetries in each of these terms. Because
the range of \\(k\\) is \\(0 \le k < N\\), while the range of \\(n\\) is \\(0
\le n < M \equiv N/2\\), we see from the symmetry properties above that we
need only perform half the computations for each sub-problem. Our
\\(\mathcal{O}[N^2]\\) computation has become \\(\mathcal{O}[M^2]\\), with
\\(M\\) half the size of \\(N\\).

But there's no reason to stop there: as long as our smaller Fourier transforms
have an even-valued \\(M\\), we can reapply this divide-and-conquer approach,
halving the computational cost each time, until our arrays are small enough
that the strategy is no longer beneficial. In the asymptotic limit, this
recursive approach scales as \\(\mathcal{O}[N\log N]\\).

This recursive algorithm can be implemented very quickly in Python, falling-
back on our slow DFT code when the size of the sub-problem becomes suitably
small:

In [4]:

    
    
    def FFT(x):
        """A recursive implementation of the 1D Cooley-Tukey FFT"""
        x = np.asarray(x, dtype=float)
        N = x.shape[0]
        
        if N % 2 > 0:
            raise ValueError("size of x must be a power of 2")
        elif N <= 32:  # this cutoff should be optimized
            return DFT_slow(x)
        else:
            X_even = FFT(x[::2])
            X_odd = FFT(x[1::2])
            factor = np.exp(-2j * np.pi * np.arange(N) / N)
            return np.concatenate([X_even + factor[:N / 2] * X_odd,
                                   X_even + factor[N / 2:] * X_odd])
    

Here we'll do a quick check that our algorithm produces the correct result:

In [5]:

    
    
    x = np.random.random(1024)
    np.allclose(FFT(x), np.fft.fft(x))
    

Out[5]:

    
    
    True
    

And we'll time this algorithm against our slow version:

In [6]:

    
    
    %timeit DFT_slow(x)
    %timeit FFT(x)
    %timeit np.fft.fft(x)
    
    
    
    10 loops, best of 3: 77.6 ms per loop
    100 loops, best of 3: 4.07 ms per loop
    10000 loops, best of 3: 24.7 µs per loop
    
    

Our calculation is faster than the naive version by over an order of
magnitude! What's more, our recursive algorithm is asymptotically
\\(\mathcal{O}[N\log N]\\): we've implemented the Fast Fourier Transform.

Note that we still haven't come close to the speed of the built-in FFT
algorithm in numpy, and this is to be expected. The FFTPACK algorithm behind
numpy's `fft` is a Fortran implementation which has received years of tweaks
and optimizations. Furthermore, our NumPy solution involves both Python-stack
recursions and the allocation of many temporary arrays, which adds significant
computation time.

A good strategy to speed up code when working with Python/NumPy is to
vectorize repeated computations where possible. We can do this, and in the
process remove our recursive function calls, and make our Python FFT even more
efficient.

## Vectorized Numpy Version¶

Notice that in the above recursive FFT implementation, at the lowest recursion
level we perform \\(N~/~32\\) identical matrix-vector products. The efficiency
of our algorithm would benefit by computing these matrix-vector products all
at once as a single matrix-matrix product. At each subsequent level of
recursion, we also perform duplicate operations which can be vectorized. NumPy
excels at this sort of operation, and we can make use of that fact to create
this vectorized version of the Fast Fourier Transform:

In [7]:

    
    
    def FFT_vectorized(x):
        """A vectorized, non-recursive version of the Cooley-Tukey FFT"""
        x = np.asarray(x, dtype=float)
        N = x.shape[0]
    
        if np.log2(N) % 1 > 0:
            raise ValueError("size of x must be a power of 2")
    
        # N_min here is equivalent to the stopping condition above,
        # and should be a power of 2
        N_min = min(N, 32)
        
        # Perform an O[N^2] DFT on all length-N_min sub-problems at once
        n = np.arange(N_min)
        k = n[:, None]
        M = np.exp(-2j * np.pi * n * k / N_min)
        X = np.dot(M, x.reshape((N_min, -1)))
    
        # build-up each level of the recursive calculation all at once
        while X.shape[0] < N:
            X_even = X[:, :X.shape[1] / 2]
            X_odd = X[:, X.shape[1] / 2:]
            factor = np.exp(-1j * np.pi * np.arange(X.shape[0])
                            / X.shape[0])[:, None]
            X = np.vstack([X_even + factor * X_odd,
                           X_even - factor * X_odd])
    
        return X.ravel()
    

Though the algorithm is a bit more opaque, it is simply a rearrangement of the
operations used in the recursive version with one exception: we exploit a
symmetry in the `factor` computation and construct only half of the array.
Again, we'll confirm that our function yields the correct result:

In [8]:

    
    
    x = np.random.random(1024)
    np.allclose(FFT_vectorized(x), np.fft.fft(x))
    

Out[8]:

    
    
    True
    

Because our algorithms are becoming much more efficient, we can use a larger
array to compare the timings, leaving out `DFT_slow`:

In [9]:

    
    
    x = np.random.random(1024 * 16)
    %timeit FFT(x)
    %timeit FFT_vectorized(x)
    %timeit np.fft.fft(x)
    
    
    
    10 loops, best of 3: 72.8 ms per loop
    100 loops, best of 3: 4.11 ms per loop
    1000 loops, best of 3: 505 µs per loop
    
    

We've improved our implementation by another order of magnitude! We're now
within about a factor of 10 of the FFTPACK benchmark, using only a couple
dozen lines of pure Python + NumPy. Though it's still no match computationally
speaking, readibility-wise the Python version is far superior to the FFTPACK
source, which you can browse [here](http://www.netlib.org/fftpack/fft.c).

So how does FFTPACK attain this last bit of speedup? Well, mainly it's just a
matter of detailed bookkeeping. FFTPACK spends a lot of time making sure to
reuse any sub-computation that can be reused. Our numpy version still involves
an excess of memory allocation and copying; in a low-level language like
Fortran it's easier to control and minimize memory use. In addition, the
Cooley-Tukey algorithm can be extended to use splits of size other than 2
(what we've implemented here is known as the _radix-2_ Cooley-Tukey FFT).
Also, other more sophisticated FFT algorithms may be used, including
fundamentally distinct approaches based on convolutions (see, e.g. Bluestein's
algorithm and Rader's algorithm). The combination of the above extensions and
techniques can lead to very fast FFTs even on arrays whose size is not a power
of two.

Though the pure-Python functions are probably not useful in practice, I hope
they've provided a bit of an intuition into what's going on in the background
of FFT-based data analysis. As data scientists, we can make-do with black-box
implementations of fundamental tools constructed by our more algorithmically-
minded colleagues, but I am a firm believer that the more understanding we
have about the low-level algorithms we're applying to our data, the better
practitioners we'll be.

_This blog post was written entirely in the IPython Notebook. The full
notebook can be downloaded [here](http://jakevdp.github.io/downloads/notebooks
/UnderstandingTheFFT.ipynb), or viewed statically [here](http://nbviewer.ipyth
on.org/url/jakevdp.github.io/downloads/notebooks/UnderstandingTheFFT.ipynb)._

Posted by Jake Vanderplas Aug 28, 2013

# Recent Posts

  * [Conda: Myths and Misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/)
  * [Analyzing Pronto CycleShare Data with Python and Pandas](https://jakevdp.github.io/blog/2015/10/17/analyzing-pronto-cycleshare-data-with-python-and-pandas/)
  * [Out-of-Core Dataframes in Python: Dask and OpenStreetMap](https://jakevdp.github.io/blog/2015/08/14/out-of-core-dataframes-in-python/)
  * [Frequentism and Bayesianism V: Model Selection](https://jakevdp.github.io/blog/2015/08/07/frequentism-and-bayesianism-5-model-selection/)
  * [Learning Seattle's Work Habits from Bicycle Counts (Updated!)](https://jakevdp.github.io/blog/2015/07/23/learning-seattles-work-habits-from-bicycle-counts/)
[Follow @jakevdp](http://twitter.com/jakevdp)

Copyright (C) 2012-2016 - Jake Vanderplas - Powered by
[Pelican](http://getpelican.com)

