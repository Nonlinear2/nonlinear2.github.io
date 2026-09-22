+++
date = '2026-08-18T16:29:41+02:00'
draft = false
title = "A proof of Rolle's lemma using Borsuk-Ulam"
weight = 2
+++

A while ago, two friends and I were looking at the Borsuk Ulam theorem and [this](https://en.wikipedia.org/wiki/Necklace_splitting_problem) beautiful application of it (I highly recommend 3blue1brown's video on the subject!). We stumbled on [this](https://en.wikipedia.org/wiki/Borsuk%E2%80%93Ulam_theorem#Equivalent_results) table in the wikipedia article. It says that the Borsuk Ulam theorem implies the Brouwer fixed point theorem[^1]. Later, we jokingly tried to prove various results using Borsuk Ulam, and here is my favourite one: an overkill proof of Rolle's lemma.

[^1]: I am still unsure about what this means. Both results are true so they surely imply each other. For now, I suppose it unformally means "Brouwer is easy to prove if you assume Borsuk-Ulam".

**Rolle's Lemma**:

Let $f: [a, b] \to \mathbb{R}$ be continuous and differentiable on $]a, b[$ with $f(a) = f(b)$. Then $\exists c \in ]a, b[$ such that $f'(c)=0$.


**Proof**:
The proof outline is as follows:
We glue both ends of $[a, b]$ together to produce a circle $\mathbb{S}^1_{[a,b]}$. Then, as $f(a) = f(b)$, $f$ remains continuous on the circle, and is differentiable everywhere except possibly at the glued $a$ and $b$ point. We can therefore apply Borsuk-Ulam, and get two antipodal points $u_0, v_0$ whose images are the same by $f$. We cut the circle in half, and pick the side that is differentiable everywhere. We flatten the half circle, and are now in the same situation as before, except the length of the interval has been cut in half. Continuing this way, the intervals shrink to a single point $c$, and we argue that this point verifies $f'(c) = 0$, proving the lemma.

_Lemma: modified Borsuk-Ulam_: Let $f: [a, b] \to \mathbb{R}$ be continuous with $f(a) = f(b)$. There exists a subinterval $[a', b']$ of length $\frac{b - a}{2}$ such that $f(a')=f(b')$.

Indeed, if we define $\mathbb{S}^1 = \mathbb{R}/(b - a)\mathbb{Z}$ and
$$
\begin{align*}
\varphi: \; \mathbb{S}^1 &\to [a, b)\\
\overline{x} &\mapsto a + x
\end{align*}
$$
where $x$ is assumed to be in $[0, b - a)$, $f$ induces a continuous map on $\mathbb{S}^1$ given by
$$
\begin{align*}
\widetilde{f}: \; \mathbb{S}^1 &\to \mathbb{R}\\
\overline{x} &\mapsto f(\varphi(\overline{x}))
\end{align*}
$$

This map is continuous on $\mathbb{S}^1$, as $f$ is continuous on $[a, b]$ and $f(a) = f(b)$.
By the Borsuk-Ulam theorem, there exists $\overline{u}, \overline{v} \in \mathbb{S}^1$ such that $\overline{v} := \overline{u} + \overline{\frac{b - a}{2}}$, we have $\widetilde{f}(\overline{u}) = \widetilde{f}(\overline{v})$.

$\overline{u}$ and $\overline{v}$ divide the circle in two arcs of length $\frac{b - a}{2}$, to finish the proof of the lemma, we only have to pick a half that doesn't contain $\overline{0}$ in its interior.


Now we can move on to the proof of Rolle's Lemma.

Applying the modified Borsuk-Ulam theorem recursively to $f$, we obtain a sequence $[a_n, b_n]$ of closed nested intervals whose length is $2^{-n}(b - a)$, and where $f(a_n) = f(b_n)$. Denote $c$ the unique element of the set $\bigcap_{n \in \mathbb{N}} [a_n, b_n]$.

We show that $f'(c) = 0$.
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

One concern is that $c$ may not lie in $]a, b[$. The only way this can happen is if the nested intervals $[a_n, b_n]$ shrink to either $a$ or $b$, and we can easily prevent this by chosing the interval closest to $\frac{a+b}{2}$ at each step where both intervals have $f$ differentiable.

$\blacksquare$

