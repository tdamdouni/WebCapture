# Optimizing Python in the Real World: NumPy, Numba, and the NUFFT

_Captured: 2017-06-10 at 13:25 from [jakevdp.github.io](https://jakevdp.github.io/blog/2015/02/24/optimizing-python-with-numpy-and-numba/)_

Donald Knuth famously quipped that "premature optimization is the root of all evil." The reasons are straightforward: optimized code tends to be much more difficult to read and debug than simpler implementations of the same algorithm, and optimizing too early leads to greater costs down the road. In the Python world, there is another cost to optimization: optimized code often is written in a compiled language like Fortran or C, and this leads to barriers to its development, use, and deployment.

Too often, tutorials about optimizing Python use trivial or toy examples which may not map well to the real world. I've certainly been [guilty](https://jakevdp.github.io/blog/2012/08/24/numba-vs-cython/) of this [myself](https://jakevdp.github.io/blog/2013/06/15/numba-vs-cython-take-2/). Here, I'm going to take a different route: in this post I will outline the process of understanding, implementing, and optimizing a non-trivial algorithm in Python, in this case the [Non-uniform Fast Fourier Transform](http://www.cims.nyu.edu/cmcl/nufft/nufft.html) (NUFFT). Along the way, we'll dig into the process of optimizing Python code, and see how a relatively straightforward pure Python implementation, with a little help from [Numba](http://numba.pydata.org), can be made to nearly match the performance of a highly-optimized Fortran implementation of the same algorithm.

## Why a Python Implementation?

First, I want to answer the inevitable question: why spend the time to make a Python implementation of an algorithm that's already out there in Fortran? The reason is that I've found in my research and teaching that pure-Python implementations of algorithms are far more valuable than C or Fortran implementations, even if they might be a bit slower. This is for a number of reasons:

  * **Pure-Python code is easier to read, understand, and contribute to.** Good Python implementations are much higher-level than C or Fortran, and abstract-away loop indices, bit twiddling, workspace arrays, and other sources of code clutter. A typical student reading good Python code can immediately understand and modify the algorithm, while the same student would be lost trying to understand typical optimized Fortran code.

  * **Pure-python packages are much easier to install than Python-wrapped C or Fortran code.** This is especially true on non-Linux systems. Fortran in particular can require some installation prerequisites that are non-trivial for many users. In practice, I've seen people give up on better tools when there is an installation barrier for those tools.

  * **Pure-python code often works for many data types.** Because of the way it is written, pure Python code is often automatically applicable to single or double precision, and perhaps even to extensions to complex numbers. For compiled packages, supporting and compiling for all possible types can be a burden.

  * **Pure-python is easier to use at scale.** Because it does not require complicated installation, pure Python packages can be much easier to install on cloud VMs and/or shared clusters for computation at scale. If you can easily pip-install a pure-Python package on a VM, then services like AWS and TravisCI are much easier to set up.

Certainly code speed will overcome these considerations if the performance gap is great enough, but I've found that for many applications a pure Python package, cleverly designed and optimized, can be made fast enough that these larger considerations win-out. The challenge is making the Python fast. We'll explore this below.

The Fast Fourier Transform (FFT) is perhaps the most important and fundamental of modern numerical algorithms. It provides a fast, method of computing the discrete Fourier transform:

You can read more about the FFT in [my previous post](https://jakevdp.github.io/blog/2013/08/28/understanding-the-fft/) on the subject.

One important limitation of the FFT is that it requires that input data be evenly-spaced: that is, we can think of the values as samples of a function where is a regular grid of points. But what about when your grid is not uniform? That is, what if you want to compute this result:

where is evaluated at an arbitrary set of points ? In this case, the FFT is no longer directly applicable, and you're stuck using a much slower direct summation.

Stuck, that is, until the NUFFT came along.

The NUFFT is an algorithm which converts the non-uniform transform into an approximate uniform transform, not with error-prone interpolation, but instead using a clever "gridding" operation motivated by the convolution theorem. If you'd like to read about the algorithm in detail, the Courant Institute's [NUFFT page](http://www.cims.nyu.edu/cmcl/nufft/nufft.html) has a nice set of resources.

Below we'll take a look at implementing this algorithm in Python.

When developing optimized code, it is important to start with something easy to make sure you're on the right track. Here we'll start with a straightforward direct version of the non-uniform Fourier transform. We'll allow non-uniform inputs , but compute the output on a grid of evenly-spaced frequencies in the range . This is what the NUFFT group calls the _Type-1 NUFFT_.

First we'll implement `nufftfreqs()`, which returns the frequency grid for a given , and `nudft()` which computes the non-uniform discrete Fourier transform using a slow direct method. The arguments for the latter include `iflag`, which is a positive or negative number indicating the desired sign of the exponent:

In [1]:
    
    
    from __future__ import print_function, division
    import numpy as np
    
    def nufftfreqs(M, df=1):
        """Compute the frequency range used in nufft for M frequency bins"""
        return df * np.arange(-(M // 2), M - (M // 2))
    
    
    def nudft(x, y, M, df=1.0, iflag=1):
        """Non-Uniform Direct Fourier Transform"""
        sign = -1 if iflag < 0 else 1
        return (1 / len(x)) * np.dot(y, np.exp(sign * 1j * nufftfreqs(M, df) * x[:, np.newaxis]))
    

Again, I can't emphasize this enough: when writing fast code, start with a slow-and-simple version of the code which you _know_ gives the correct result, and then optimize from there.
    
    
    # Install nufft from http://github.com/dfm/python-nufft/
    from nufft import nufft1 as nufft_fortran
    
    x = 100 * np.random.random(1000)
    y = np.sin(x)
    
    Y1 = nudft(x, y, 1000)
    Y2 = nufft_fortran(x, y, 1000)
    
    np.allclose(Y1, Y2)
    

In [4]:
    
    
    def _compute_grid_params(M, eps):
        # Choose Msp & tau from eps following Dutt & Rokhlin (1993)
        if eps <= 1E-33 or eps >= 1E-1:
            raise ValueError("eps = {0:.0e}; must satisfy "
                             "1e-33 < eps < 1e-1.".format(eps))
        ratio = 2 if eps > 1E-11 else 3
        Msp = int(-np.log(eps) / (np.pi * (ratio - 1) / (ratio - 0.5)) + 0.5)
        Mr = max(ratio * M, 2 * Msp)
        lambda_ = Msp / (ratio * (ratio - 0.5))
        tau = np.pi * lambda_ / M ** 2
        return Msp, Mr, tau
    
    
    def nufft_python(x, c, M, df=1.0, eps=1E-15, iflag=1):
        """Fast Non-Uniform Fourier Transform with Python"""
        Msp, Mr, tau = _compute_grid_params(M, eps)
        N = len(x)
    
        # Construct the convolved grid
        ftau = np.zeros(Mr, dtype=c.dtype)
        Mr = ftau.shape[0]
        hx = 2 * np.pi / Mr
        mm = np.arange(-Msp, Msp)
        for i in range(N):
            xi = (x[i] * df) % (2 * np.pi)
            m = 1 + int(xi // hx)
            spread = np.exp(-0.25 * (xi - hx * (m + mm)) ** 2 / tau)
            ftau[(m + mm) % Mr] += c[i] * spread
    
        # Compute the FFT on the convolved grid
        if iflag < 0:
            Ftau = (1 / Mr) * np.fft.fft(ftau)
        else:
            Ftau = np.fft.ifft(ftau)
        Ftau = np.concatenate([Ftau[-(M//2):], Ftau[:M//2 + M % 2]])
    
        # Deconvolve the grid using convolution theorem
        k = nufftfreqs(M)
        return (1 / N) * np.sqrt(np.pi / tau) * np.exp(tau * k ** 2) * Ftau
    

In [5]:
    
    
    from time import time
    
    def test_nufft(nufft_func, M=1000, Mtime=100000):
        # Test vs the direct method
        print(30 * '-')
        name = {'nufft1':'nufft_fortran'}.get(nufft_func.__name__,
                                              nufft_func.__name__)
        print("testing {0}".format(name))
        rng = np.random.RandomState(0)
        x = 100 * rng.rand(M + 1)
        y = np.sin(x)
        for df in [1, 2.0]:
            for iflag in [1, -1]:
                F1 = nudft(x, y, M, df=df, iflag=iflag)
                F2 = nufft_func(x, y, M, df=df, iflag=iflag)
                assert np.allclose(F1, F2)
        print("- Results match the DFT")
        
        # Time the nufft function
        x = 100 * rng.rand(Mtime)
        y = np.sin(x)
        times = []
        for i in range(5):
            t0 = time()
            F = nufft_func(x, y, Mtime)
            t1 = time()
            times.append(t1 - t0)
        print("- Execution time (M={0}): {1:.2g} sec".format(Mtime, np.median(times)))
    

We know that our Python function is slow, but we'd like to determine _where_ this speed bottleneck lies. One convenient way to do this is with the `line_profiler` utility, a Python/IPython addon which can be installed using
    
    
    $ pip install line_profiler

Once it's installed, we can load the line profiler extension into the IPython notebook using the `%load_ext` magic function:
    
    
    *** Profile printout saved to text file 'lp_results.txt'. 
    Timer unit: 1e-06 s
    
    Total time: 0.040097 s
    File: <ipython-input-4-02aa33b61f03>
    Function: nufft_python at line 14
    
    Line #      Hits         Time  Per Hit   % Time  Line Contents
    ==============================================================
        14                                           def nufft_python(x, c, M, df=1.0, eps=1E-15, iflag=1):
        15                                               """Fast Non-Uniform Fourier Transform with Python"""
        16         1           41     41.0      0.1      Msp, Mr, tau = _compute_grid_params(M, eps)
        17         1            3      3.0      0.0      N = len(x)
        18                                           
        19                                               # Construct the convolved grid
        20         1           19     19.0      0.0      ftau = np.zeros(Mr, dtype=c.dtype)
        21         1            2      2.0      0.0      Mr = ftau.shape[0]
        22         1            3      3.0      0.0      hx = 2 * np.pi / Mr
        23         1           11     11.0      0.0      mm = np.arange(-Msp, Msp)
        24      1001         1493      1.5      3.7      for i in range(N):
        25      1000         2801      2.8      7.0          xi = (x[i] * df) % (2 * np.pi)
        26      1000         3024      3.0      7.5          m = 1 + int(xi // hx)
        27      1000        21048     21.0     52.5          spread = np.exp(-0.25 * (xi - hx * (m + mm)) ** 2 / tau)
        28      1000        11406     11.4     28.4          ftau[(m + mm) % Mr] += c[i] * spread
        29                                           
        30                                               # Compute the FFT on the convolved grid
        31         1            2      2.0      0.0      if iflag < 0:
        32                                                   Ftau = (1 / Mr) * np.fft.fft(ftau)
        33                                               else:
        34         1          183    183.0      0.5          Ftau = np.fft.ifft(ftau)
        35         1           15     15.0      0.0      Ftau = np.concatenate([Ftau[-(M//2):], Ftau[:M//2 + M % 2]])
        36                                           
        37                                               # Deconvolve the grid using convolution theorem
        38         1           14     14.0      0.0      k = nufftfreqs(M)
        39         1           32     32.0      0.1      return (1 / N) * np.sqrt(np.pi / tau) * np.exp(tau * k ** 2) * Ftau

The output shows us where, line-by-line, the algorithm is spending the most time. We see that nearly 99% of the execution time is being spent in the single `for` loop at the center of our code. The loop is so expensive that even the FFT computation is just a trivial piece of the cost! This is actually pretty typical: due to dynamic typing, loops are generally very slow in Python.

One of the surest strategies for speeding-up your code is to use broadcasting tricks in NumPy to remove these kinds of large loops: you can read one of my course lectures on the subject [here](http://nbviewer.ipython.org/url/www.astro.washington.edu/users/vanderplas/Astr599_2014/notebooks/11_EfficientNumpy.ipynb). We'll do this next.

Let's rewrite the above implementation and use broadcasting tricks to elliminate the loops. Because of the structure of this problem, the approach is a bit complicated here, but it turns out that we can take advantage here of the little-known `at()` method of NumPy's ufunc (available since NumPy 1.8). Briefly,
    
    
    >>> np.add.at(x, i, y)

is similar to
    
    
    >>> x[i] += y

but works as desired even if the incides `i` have duplicate entries.

Using this, we can adjust our implementation as follows:

In [9]:
    
    
    def nufft_numpy(x, y, M, df=1.0, iflag=1, eps=1E-15):
        """Fast Non-Uniform Fourier Transform"""
        Msp, Mr, tau = _compute_grid_params(M, eps)
        N = len(x)
    
        # Construct the convolved grid ftau:
        # this replaces the loop used above
        ftau = np.zeros(Mr, dtype=y.dtype)
        hx = 2 * np.pi / Mr
        xmod = (x * df) % (2 * np.pi)
        m = 1 + (xmod // hx).astype(int)
        mm = np.arange(-Msp, Msp)
        mpmm = m + mm[:, np.newaxis]
        spread = y * np.exp(-0.25 * (xmod - hx * mpmm) ** 2 / tau)
        np.add.at(ftau, mpmm % Mr, spread)
    
        # Compute the FFT on the convolved grid
        if iflag < 0:
            Ftau = (1 / Mr) * np.fft.fft(ftau)
        else:
            Ftau = np.fft.ifft(ftau)
        Ftau = np.concatenate([Ftau[-(M//2):], Ftau[:M//2 + M % 2]])
    
        # Deconvolve the grid using convolution theorem
        k = nufftfreqs(M)
        return (1 / N) * np.sqrt(np.pi / tau) * np.exp(tau * k ** 2) * Ftau
    
    
    
    test_nufft(nufft_numpy)
    test_nufft(nufft_python)
    test_nufft(nufft_fortran)
    
    
    
    ------------------------------
    testing nufft_numpy
    - Results match the DFT
    - Execution time (M=100000): 0.45 sec
    ------------------------------
    testing nufft_python
    - Results match the DFT
    - Execution time (M=100000): 1.6 sec
    ------------------------------
    testing nufft_fortran
    - Results match the DFT
    - Execution time (M=100000): 0.044 sec
    

When NumPy broadcasting tricks aren't enough, there are a few options: you can write Fortran or C code directly, you can use [Cython](http://cython.org), [Weave](http://docs.scipy.org/doc/scipy/reference/tutorial/weave.html), or other tools as a bridge to include compiled snippets in your script, or you can use a tool like [Numba](http://cython.org) to speed-up your loops without ever leaving Python.

Numba is a slick tool which runs Python functions through an LLVM just-in-time (JIT) compiler, leading to orders-of-magnitude faster code for certain operations. In this case, we need to optimize what amounts to a nested for-loop, so Numba fits the bill perfectly. For clarity, we'll pull-out the grid construction code that we want to optimize, and write it as follows:

In [11]:
    
    
    import numba
    
    # nopython=True means an error will be raised
    # if fast compilation is not possible.
    @numba.jit(nopython=True)
    def build_grid(x, c, tau, Msp, ftau):
        Mr = ftau.shape[0]
        hx = 2 * np.pi / Mr
        for i in range(x.shape[0]):
            xi = x[i] % (2 * np.pi)
            m = 1 + int(xi // hx)
            for mm in range(-Msp, Msp):
                ftau[(m + mm) % Mr] += c[i] * np.exp(-0.25 * (xi - hx * (m + mm)) ** 2 / tau)
        return ftau
    
    
    def nufft_numba(x, c, M, df=1.0, eps=1E-15, iflag=1):
        """Fast Non-Uniform Fourier Transform with Numba"""
        Msp, Mr, tau = _compute_grid_params(M, eps)
        N = len(x)
    
        # Construct the convolved grid
        ftau = build_grid(x * df, c, tau, Msp,
                          np.zeros(Mr, dtype=c.dtype))
    
        # Compute the FFT on the convolved grid
        if iflag < 0:
            Ftau = (1 / Mr) * np.fft.fft(ftau)
        else:
            Ftau = np.fft.ifft(ftau)
        Ftau = np.concatenate([Ftau[-(M//2):], Ftau[:M//2 + M % 2]])
    
        # Deconvolve the grid using convolution theorem
        k = nufftfreqs(M)
        return (1 / N) * np.sqrt(np.pi / tau) * np.exp(tau * k ** 2) * Ftau
    

Much better! We're now within about a factor of 3 of the Fortran speed, and we're still writing pure Python!

Having plucked all the low-hanging fruit, any further optimization will now be very low-level: that is, thinking about things like reduction of the number of `exp()` evaluations through application of mathematical identities. This type of careful logic is one reason the Fortran implementation is so fast, and many of these low-level strategies are discussed in the NUFFT paper linked above.

To gain some more speed, we can follow their advice and optimize the expressions at this level by precomputing expensive expressions and recombining these expressions later: This obfuscates the logic of the algorithm a bit, but it does lead to some faster execution. Here is an example of this:

In [13]:
    
    
    import numba
    
    @numba.jit(nopython=True)
    def build_grid_fast(x, c, tau, Msp, ftau, E3):
        Mr = ftau.shape[0]
        hx = 2 * np.pi / Mr
        
        # precompute some exponents
        for j in range(Msp + 1):
            E3[j] = np.exp(-(np.pi * j / Mr) ** 2 / tau)
            
        # spread values onto ftau
        for i in range(x.shape[0]):
            xi = x[i] % (2 * np.pi)
            m = 1 + int(xi // hx)
            xi = (xi - hx * m)
            E1 = np.exp(-0.25 * xi ** 2 / tau)
            E2 = np.exp((xi * np.pi) / (Mr * tau))
            E2mm = 1
            for mm in range(Msp):
                ftau[(m + mm) % Mr] += c[i] * E1 * E2mm * E3[mm]
                E2mm *= E2
                ftau[(m - mm - 1) % Mr] += c[i] * E1 / E2mm * E3[mm + 1]
        return ftau
    
    
    def nufft_numba_fast(x, c, M, df=1.0, eps=1E-15, iflag=1):
        """Fast Non-Uniform Fourier Transform with Numba"""
        Msp, Mr, tau = _compute_grid_params(M, eps)
        N = len(x)
    
        # Construct the convolved grid
        ftau = build_grid_fast(x * df, c, tau, Msp,
                               np.zeros(Mr, dtype=c.dtype),
                               np.zeros(Msp + 1, dtype=x.dtype))
    
        # Compute the FFT on the convolved grid
        if iflag < 0:
            Ftau = (1 / Mr) * np.fft.fft(ftau)
        else:
            Ftau = np.fft.ifft(ftau)
        Ftau = np.concatenate([Ftau[-(M//2):], Ftau[:M//2 + M % 2]])
    
        # Deconvolve the grid using convolution theorem
        k = nufftfreqs(M)
        return (1 / N) * np.sqrt(np.pi / tau) * np.exp(tau * k ** 2) * Ftau
    
    
    
    %matplotlib inline
    import matplotlib.pyplot as plt
    # use seaborn for nice default plot settings
    import seaborn; seaborn.set()
    

In [16]:
    
    
    Mrange = (2 ** np.arange(3, 18)).astype(int)
    
    t_python = []
    t_numpy = []
    t_numba = []
    t_numba_fast = []
    t_fortran = []
    
    for M in Mrange:
        x = 100 * np.random.random(M)
        c = np.sin(x)
        
        t1 = %timeit -oq nufft_python(x, c, M)
        t2 = %timeit -oq nufft_numpy(x, c, M)
        t3 = %timeit -oq nufft_numba(x, c, M)
        t4 = %timeit -oq nufft_numba_fast(x, c, M)
        t5 = %timeit -oq nufft_fortran(x, c, M)
        
        t_python.append(t1.best)
        t_numpy.append(t2.best)
        t_numba.append(t3.best)
        t_numba_fast.append(t4.best)
        t_fortran.append(t5.best)
    
    
    
    plt.loglog(Mrange, t_python, label='python')
    plt.loglog(Mrange, t_numpy, label='numpy')
    plt.loglog(Mrange, t_numba, label='numba #1')
    plt.loglog(Mrange, t_numba_fast, label='numba #2')
    plt.loglog(Mrange, t_fortran, label='fortran')
    plt.legend(loc='upper left')
    plt.xlabel('Number of Elements')
    plt.ylabel('Execution Time (s)');
    

![](data:image/png;base64,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
TzywRwAAAABJRU5ErkJggg==)

I hope you've enjoyed this exploration of how to write fast numerical code in pure Python. As you think about writing efficient implementations of useful algorithms, I invite you to consider the points I listed above: in particular, how difficult will it be for your users to install, read, modify, and contribute to your code? In the long run, this may be much more important than shaving a few milliseconds off the execution time. Writing a fast implementation of a useful algorithm is an excellent and useful pursuit, but we should be careful to not forget the costs that come along with such optimization.

If you're interested in using the pure-Python NUFFT implementation, I've adapted much of the above code in a repository at <http://github.com/jakevdp/nufftpy/>. It contains a packaged and unit-tested version of some of the above code, as well as a (hopefully) growing compendium of related routines.
