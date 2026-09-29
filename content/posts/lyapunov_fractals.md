+++
date = '2026-08-18T22:34:35+02:00'
draft = false
title = 'Lyapunov Fractals'
+++

As you can see by my profile picture and website design, I'm particularly fond of Lyapunov fractals. Writing [a real time renderer](https://github.com/Nonlinear2/lyapunov-fractals) was my first attempt to learn about GPU programming, and was inspired by [this](https://youtube...) video by desdenova. 


In the following section we will discuss 2D lyapunov fractals. The generalization to higher dimensions is quite simple as you just need to allow more coordinates in the pattern, and compute the modified logistic sequence values accordingly.

## Theory
A 2D lyapunov fractal is created by computing the _lyapunov exponent_ for each screen pixel of a modified logistic sequence.

### Modified Logistic sequences

We call _pattern_ a chain of "x" and "y" characters, such as "xyyyxyxx".

Given a pattern, a real number $v_0$, and a value for $x$ and $y$, we define a sequence $f^N(v_0)$ by the relation

$$f^{N}(v_0) = \begin{cases} v_0 & \text{if } N = 0 \\ r_{x, y}(N-1) \cdot  f^{N-1}(v_0) \cdot (1 - f^{N-1}(v_0)) & \text{if } N > 0\end{cases}$$

where $r_{x, y}(N) = \text{pattern}[N \; \;\text{mod} \; \text{length(pattern)}]$

### The lyapunov exponent

For a small enough initial distance $\epsilon$ between two neighbouring points, we will assume that the distance between each sequence iteration evolves like an exponential function:

$$|f^N(v_0) - f^N(v_0 + \epsilon)| \approx \epsilon e^{\lambda N}$$

We can therefore define the Lyapunov exponent $\lambda$ to be:

$$\begin{align}
\lambda &= \lim_{N \to +\infty}\lim_{\epsilon \to 0}\frac{1}{N}\ln(\frac{|f^N(v_0) - f^N(v_0 + \epsilon)|}{\epsilon})\\
&= \lim_{N \to +\infty}\frac{1}{N}\ln|\frac{df^N}{dx}|_{v_0}\\
&= \lim_{N \to +\infty}\frac{1}{N}\ln\left[|\frac{df}{dx}|_{f^{N-1}(v_0)} \cdot |\frac{df^{N-1}}{dx}|_{f^{N-2}(v_0)} \right]\\
&= \lim_{N \to +\infty}\frac{1}{N}\ln\left[|\frac{df}{dx}|_{f^{N-1}(v_0)} \cdot |\frac{df}{dx}|_{f^{N-2}(v_0)} \dots |\frac{df}{dx}|_{v_0} \right]\\
&= \lim_{N \to +\infty}\frac{1}{N} \sum_{n=1}^{N-1}\ln|\frac{df}{dx}|_{f^{n}(v_0)}
\end{align}$$

To compute the Lyapunov exponent numerically, we can truncate the series at a large value of $N$.

So briefly, the lyapunov exponent $\lambda$ is a measure of how quickly an infinitesimal change in the initial condition $v_0$ grows over time. If the Lyapunov exponent is positive, nearby points are stretched apart, and if it is negative, they are compressed together.


### Fractal algorithm

We first associate the pixels of the screen to a grid of coordinates between 0 and 4 (this is a range on which the logistic sequence is stable).

Then for each pixel on the screen:
1. We get the $x$ and $y$ coordinates corresponding to the pixel position.
2. We compute the lyapunov exponent of the sequence $(f^N(0.5))$
3. Then, we color the pixel according to the value of the lyapunov exponent.

This algorithm is generalizable to higher dimensions than 2 by adding new letters in the logistic sequence pattern, and cycling $r$ through the corresponding space coordinates.

In our case, $f(x) = rx(1-x)$ so $\frac{df}{dx} = r(1-2x)$. Moreover, as we color our pixels by comparing the values of $\lambda$ at each pixel, the constant factor $\frac{1}{N}$ does not change the resulting image. We can therefore discard it and write:

$$\lambda'_N = \sum_{n=1}^{N}\ln|r_n(1-2f^{n}(v_0))|$$

Interestingly, the diagonal $x = y$ of any 2D lyapunov fractal is always the same, as the pattern doesn't influence the sequence. The color of the diagonal is given by the lyapunov exponents of the classic logistic sequence for values of $r$ going from 0 to 4.

Here is the kernel that runs for each image pixel:
```python
for i in range(num_iter):
    r = (x, y, z)[sequence[i%len_sequence]]
    x_n = r*x_n*(1-x_n)
    lambda_N += log(abs(r*(1-2*x_n)))
space[pos] = lambda_N
```
