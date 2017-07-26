# Understanding the FFT Algorithm

_Captured: 2016-11-18 at 14:29 from [jakevdp.github.io](http://jakevdp.github.io/blog/2013/08/28/understanding-the-fft/)_

The Fast Fourier Transform (FFT) is one of the most important algorithms in signal processing and data analysis. I've used it for years, but having no formal computer science background, It occurred to me this week that I've never thought to ask _how_ the FFT computes the discrete Fourier transform so quickly. I dusted off an old algorithms book and looked into it, and enjoyed reading about the deceptively simple computational trick that JW Cooley and John Tukey outlined in their classic [1965 paper](http://www.ams.org/journals/mcom/1965-19-090/S0025-5718-1965-0178586-1/) introducing the subject.

The goal of this post is to dive into the Cooley-Tukey FFT algorithm, explaining the symmetries that lead to it, and to show some straightforward Python implementations putting the theory into practice. My hope is that this exploration will give data scientists like myself a more complete picture of what's going on in the background of the algorithms we use.

The FFT is a fast, algorithm to compute the Discrete Fourier Transform (DFT), which naively is an computation. The DFT, like the more familiar continuous version of the Fourier transform, has a forward and inverse form which are defined as follows:

The transformation from is a translation from configuration space to frequency space, and can be very useful in both exploring the power spectrum of a signal, and also for transforming certain problems for more efficient computation. For some examples of this in action, you can check out Chapter 10 of our upcoming Astronomy/Statistics book, with figures and Python source code available [here](http://www.astroml.org/book_figures/chapter10/). For an example of the FFT being used to simplify an otherwise difficult differential equation integration, see my post on [Solving the Schrodinger Equation in Python](http://jakevdp.github.io/blog/2012/09/05/quantum-python/).

Because of the importance of the FFT in so many fields, Python contains many standard tools and wrappers to compute this. Both NumPy and SciPy have wrappers of the extremely well-tested FFTPACK library, found in the submodules `numpy.fft` and `scipy.fftpack` respectively. The fastest FFT I am aware of is in the [FFTW](http://www.fftw.org/) package, which is also available in Python via the [PyFFTW](https://pypi.python.org/pypi/pyFFTW) package.

For the moment, though, let's leave these implementations aside and ask how we might compute the FFT in Python from scratch.

For simplicity, we'll concern ourself only with the forward transform, as the inverse transform can be implemented in a very similar manner. Taking a look at the DFT expression above, we see that it is nothing more than a straightforward linear operation: a matrix-vector multiplication of ,

With this in mind, we can compute the DFT using simple matrix multiplication as follows:
    
    
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
    
    
    x = np.random.random(1024)
    np.allclose(DFT_slow(x), np.fft.fft(x))
    

Just to confirm the sluggishness of our algorithm, we can compare the execution times of these two approaches:
    
    
    %timeit DFT_slow(x)
    %timeit np.fft.fft(x)
    

We are over 1000 times slower, which is to be expected for such a simplistic implementation. But that's not the worst of it. For an input vector of length , the FFT algorithm scales as , while our slow algorithm scales as . That means that for elements, we'd expect the FFT to complete in somewhere around 50 ms, while our slow algorithm would take nearly 20 hours!

So how does the FFT accomplish this speedup? The answer lies in exploiting symmetry.

One of the most important tools in the belt of an algorithm-builder is to exploit symmetries of a problem. If you can show analytically that one piece of a problem is simply related to another, you can compute the subresult only once and save that computational cost. Cooley and Tukey used exactly this approach in deriving the FFT.

The last line shows a nice symmetry property of the DFT:

By a simple extension,

for any integer . As we'll see below, this symmetry can be exploited to compute the DFT much more quickly.

Cooley and Tukey showed that it's possible to divide the DFT computation into two smaller parts. From the definition of the DFT we have:

Xk=∑n=0N−1xn⋅e−i2πkn/N=∑m=0N/2−1x2m⋅e−i2πk(2m)/N+∑m=0N/2−1x2m+1⋅e−i2πk(2m+1)/N=∑m=0N/2−1x2m⋅e−i2πkm/(N/2)+e−i2πk/N∑m=0N/2−1x2m+1⋅e−i2πkm/(N/2)

We've split the single Discrete Fourier transform into two terms which themselves look very similar to smaller Discrete Fourier Transforms, one on the odd-numbered values, and one on the even-numbered values. So far, however, we haven't saved any computational cycles. Each term consists of computations, for a total of .

The trick comes in making use of symmetries in each of these terms. Because the range of is , while the range of is , we see from the symmetry properties above that we need only perform half the computations for each sub-problem. Our computation has become , with half the size of .

But there's no reason to stop there: as long as our smaller Fourier transforms have an even-valued , we can reapply this divide-and-conquer approach, halving the computational cost each time, until our arrays are small enough that the strategy is no longer beneficial. In the asymptotic limit, this recursive approach scales as .

This recursive algorithm can be implemented very quickly in Python, falling-back on our slow DFT code when the size of the sub-problem becomes suitably small:

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
    
    
    x = np.random.random(1024)
    np.allclose(FFT(x), np.fft.fft(x))
    

And we'll time this algorithm against our slow version:
    
    
    %timeit DFT_slow(x)
    %timeit FFT(x)
    %timeit np.fft.fft(x)
    

Our calculation is faster than the naive version by over an order of magnitude! What's more, our recursive algorithm is asymptotically : we've implemented the Fast Fourier Transform.

Note that we still haven't come close to the speed of the built-in FFT algorithm in numpy, and this is to be expected. The FFTPACK algorithm behind numpy's `fft` is a Fortran implementation which has received years of tweaks and optimizations. Furthermore, our NumPy solution involves both Python-stack recursions and the allocation of many temporary arrays, which adds significant computation time.

A good strategy to speed up code when working with Python/NumPy is to vectorize repeated computations where possible. We can do this, and in the process remove our recursive function calls, and make our Python FFT even more efficient.

Notice that in the above recursive FFT implementation, at the lowest recursion level we perform identical matrix-vector products. The efficiency of our algorithm would benefit by computing these matrix-vector products all at once as a single matrix-matrix product. At each subsequent level of recursion, we also perform duplicate operations which can be vectorized. NumPy excels at this sort of operation, and we can make use of that fact to create this vectorized version of the Fast Fourier Transform:

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
    

Though the algorithm is a bit more opaque, it is simply a rearrangement of the operations used in the recursive version with one exception: we exploit a symmetry in the `factor` computation and construct only half of the array. Again, we'll confirm that our function yields the correct result:
    
    
    x = np.random.random(1024)
    np.allclose(FFT_vectorized(x), np.fft.fft(x))
    

Because our algorithms are becoming much more efficient, we can use a larger array to compare the timings, leaving out `DFT_slow`:
    
    
    x = np.random.random(1024 * 16)
    %timeit FFT(x)
    %timeit FFT_vectorized(x)
    %timeit np.fft.fft(x)
    

We've improved our implementation by another order of magnitude! We're now within about a factor of 10 of the FFTPACK benchmark, using only a couple dozen lines of pure Python + NumPy. Though it's still no match computationally speaking, readibility-wise the Python version is far superior to the FFTPACK source, which you can browse [here](http://www.netlib.org/fftpack/fft.c).

So how does FFTPACK attain this last bit of speedup? Well, mainly it's just a matter of detailed bookkeeping. FFTPACK spends a lot of time making sure to reuse any sub-computation that can be reused. Our numpy version still involves an excess of memory allocation and copying; in a low-level language like Fortran it's easier to control and minimize memory use. In addition, the Cooley-Tukey algorithm can be extended to use splits of size other than 2 (what we've implemented here is known as the _radix-2_ Cooley-Tukey FFT). Also, other more sophisticated FFT algorithms may be used, including fundamentally distinct approaches based on convolutions (see, e.g. Bluestein's algorithm and Rader's algorithm). The combination of the above extensions and techniques can lead to very fast FFTs even on arrays whose size is not a power of two.

Though the pure-Python functions are probably not useful in practice, I hope they've provided a bit of an intuition into what's going on in the background of FFT-based data analysis. As data scientists, we can make-do with black-box implementations of fundamental tools constructed by our more algorithmically-minded colleagues, but I am a firm believer that the more understanding we have about the low-level algorithms we're applying to our data, the better practitioners we'll be.
