# ~~Distributed~~ High-performance Computing

### [Slides](https://docs.google.com/presentation/d/1Qamkuq7xH4dV0J9bOy-MAFnGLIiZMKH229A9o6Ux_58/edit?usp=sharing)

## Installation Instructions

We will use Julia and R. Please run ``Pkg.update()`` in Julia to get recent updates to JuMP.

You will need the ``GZip`` Julia package to run the parallel computing example (install with ``Pkg.add("GZip")``).

## Assignment

We've implemented a basic **[gradient descent]** algorithm in **[gradient.jl]**. The code prints iteration data, execution time, and then a *profile* of the execution time. Your output should look like:

```
...
Iter: 220000 Obj. val: 1.3117761223644775e-6 Gradient norm: 0.00010665354404437781
Iter: 225000 Obj. val: 1.2752254793258623e-6 Gradient norm: 0.00034766759251038073
Iter: 230000 Obj. val: 1.2405145432051558e-6 Gradient norm: 0.00011238057512221296
Converged
elapsed time: 31.756677491 seconds (8232411136 bytes allocated)
 Count File                       Function                                 Line
  5656 ...performance/gradient.jl f                                           4
   173 ...performance/gradient.jl fgrad                                       5
   128 ...performance/gradient.jl gradDescent                                15
     4 ...performance/gradient.jl gradDescent                                16
    28 ...performance/gradient.jl gradDescent                                19
 11640 ...performance/gradient.jl gradDescent                                22
 ...
```
*Update:* Profiling functionality is not working on Windows. Using the most recent script, you will just see ``elapsed time``.

**Submit** the line starting with ``elapsed time``. The profiler in Julia works by taking a sample every millisecond and recording which line of code is currently being executed. For example, the first line of the output means that in 5,656 of the samples (5.6 seconds), Julia was executing ``f`` at line 4 of gradient.jl. Which lines of code are dominating the execution time?

**Challenge**: Try to make the code run twice as fast. Some possible approaches include reusing calculations and memory instead of computing ``Q*x`` multiple times and creating new vectors on each iteration. Feel free to restructure the code or implement your own version. Submit your new solution and execution time. Don't spend too much time on this; we will work on this example in the class. **[Suggested reading]**

If you would like to follow along with the parallel computing example in class, run the ``data.R`` script in this directory. It will take a few minutes to run and will generate a ``tripsbydate`` subdirectory with a large number of files called, for example, ``2011-10-12.csv.gz``. No submission is necessary.

[gradient.jl]: https://github.com/IainNZ/ORSoftwareTools2014/blob/master/DistribComputing/performance/gradient.jl
[gradient descent]: http://en.wikipedia.org/wiki/Gradient_descent
[suggested reading]: http://julialang.org/blog/2013/09/fast-numeric/
