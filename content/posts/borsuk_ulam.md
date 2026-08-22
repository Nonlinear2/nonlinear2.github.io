+++
date = '2026-08-18T16:29:41+02:00'
draft = false
title = "A proof of Rolle's lemma using Borsuk-Ulam"
weight = 2
+++

A while ago, two friends and I were looking at the Borsuk Ulam theorem and [this](https://en.wikipedia.org/wiki/Necklace_splitting_problem) beautiful application of it (I highly recommend 3blue1brown's video on the subject!). We stumbled on [this](https://en.wikipedia.org/wiki/Borsuk%E2%80%93Ulam_theorem#Equivalent_results) table in the wikipedia article. It says that the Borsuk Ulam theorem implies the Brouwer fixed point theorem[^1]. Later, we jokingly tried to prove various results using Borsuk Ulam, and here is my favourite one: an overkill proof of Rolle's lemma.

[^1]: I am still unsure about what this means. Both results are true so they surely imply each other. For now, I suppose it unformally means "Brouwer is easy to prove if you assume Borsuk-Ulam".

**Lemma**:

Let $a, b \in \mathbb{R}$ be such that $a < b$ and let $f: [a, b] \to \mathbb{R}$ be a function that is continuous on $[a, b]$ and differentiable on $]a, b[$, such that $f(a) = f(b)$. Then $\exists c \in ]a, b[$ such that $f'(c)=0$.


**Proof**:

First, we define $\mathbb{S}^1_{(0)}$ to be $\mathbb{R}/(b - a)\mathbb{Z}$.
Define the map

$$
\begin{align*}
\varphi: \; \mathbb{S}^1 &\to [a, b)\\
\overline{x} &\mapsto a + x
\end{align*}
$$
where $x$ is assumed to be in $[0, b - a)$.

Now, $f$ induces a continuous map on $\mathbb{S}^1$ given by

$$
\begin{align*}
\widetilde{f}: \; \mathbb{S}^1 &\to \mathbb{R}\\
\overline{x} &\mapsto f(\varphi(\overline{x}))
\end{align*}
$$

This map is continuous on $\mathbb{S}^1$, as $f$ is continuous on $[a, b]$ and $f(a) = f(b)$.

By the Borsuk-Ulam theorem, there exists $u_0 \in \mathbb{S}^1$ such that, setting $v_0 := u_0 + \frac{b - a}{2}$, we have $\widetilde{f}(u_0) = \widetilde{f}(v_0)$. Moreover, $f$ is supposed to be differentiable everywhere on $]a, b[$, so the only point where $\widetilde{f}$ may not be differentiable is at $\overline{0}$.

Now $u_0$ and $v_0$ divide the circle in two open arcs of length $\frac{b - a}{2}$, and $f$ is differentiable everywhere on at least one of these two parts.
We denote $[a_1, b_1] \subset [a, b]$ the corresponding interval. we now proceed by induction, and define:

$$\mathbb{S}^1_{(1)} = \mathbb{R}/(b_1 - a_1)\mathbb{Z}$$
and 
$$
\begin{align*}
\varphi_1: \; \mathbb{S}^1_{(1)} &\to [a_1, b_1)\\
\overline{x} &\mapsto a_1 + x
\end{align*}
$$

$$
\begin{align*}
\widetilde{f_1}: \; \mathbb{S}^1_{(1)} &\to \mathbb{R}\\
\overline{x} &\mapsto f(\varphi_1(\overline{x}))
\end{align*}
$$

on which we apply the Borsuk-Ulam theorem, and obtain $u_1 \in \mathbb{S}^1_{(1)}$ such that $\widetilde{f}(u_1) = \widetilde{f}(u_1 + \frac{b_1 - a_1}{2})$ as well as $[a_2, b_2] \subset [a_1, b_1]$ the corresponding interval.

We can thus form a sequence $[a_n, b_n]$ of closed nested intervals whose length is $2^{-n}(b - a)$. Denote $c$ the unique element of the set $\bigcap_{n \in \mathbb{N}} [a_n, b_n]$.

We will show that $f'(c) = 0$.

$$
\begin{align*}
0
&= f(b_n) - f(a_n)\\
&= [f(c) + f'(c)(b_n-c) + \varepsilon(b_n-c)(b_n-c)] - [f(c) + f'(c)(a_n-c) + \varepsilon(a_n-c)(a_n-c)]\\
&= f'(c)(b_n-a_n) + \varepsilon(b_n-c)(b_n-c) - \varepsilon(a_n-c)(a_n-c)\\
&= f'(c)+ \varepsilon(b_n-c)\frac{b_n-c}{b_n-a_n} - \varepsilon(a_n-c)\frac{a_n-c}{b_n-a_n}\\
\end{align*}
$$

And thus taking $n$ to $+\infty$, as $\frac{b_n-c}{b_n-a_n}$ and $\frac{a_n-c}{b_n-a_n}$ are bounded between $-1$ and $1$, we find $f'(c) = 0$.

A concern is that $c$ may not lie in $]a, b[$, as must be proven. The only way this can happen is if the nested intervals $[a_n, b_n]$ shrink to either $a$ or $b$, and we can easily prevent this by chosing the interval closest to $\frac{a+b}{2}$ at each step where both intervals have $f$ differentiable.

$\blacksquare$

