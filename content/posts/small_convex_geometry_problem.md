+++
date = '2026-11-06T17:19:24+01:00'
draft = false
title = 'A small problem on convex geometry'
+++

**Proposition**: Let $C \subset \mathbb{R}^d$ be a closed convex set containing 0 and a basis of $\mathbb{R}^d$, then $C$ has non empty interior.


The following proof is overkill. An easier way would be to look at the $d$-dimensional simplex, and show it has non empty interior as a finite intersection of open sets. I prefer the geometric interpretation of the following proof, though.

**Solution**:

Let $C \subset \mathbb{R}^d$ be convex and containing $0$, and $e_1, \dots, e_d$ a basis of $\mathbb{R}^d$. Denote by $S$ the set of $d\times d$ diagonal matrices where each entry $a$ has the same nonzero integer magnitude. Then 
$$\bigcup_{A \in S} T_A(C) = \mathbb{R}^d$$
where $T_A$ is the linear transformation associated with $A$. Indeed, if $x \in \mathbb{R}^d$, $x = \sum_{i = 1}^d x_i e_i$. Write $M = \mathrm{max}(\{1\} \cup \{|x_i|, i \le d\})$. Then
\[
\begin{align*}
x &= \sum_{i = 1}^d \frac{x_i}{d\lceil M \rceil} d\lceil M \rceil \mathrm{sign}(x_i) e_i\\
  &= \sum_{i = 1}^d \alpha_i d\lceil M \rceil \mathrm{sign}(x_i) e_i
\end{align*}
\]
where $\sum_{i = 1}^d \alpha_i \le 1$. So $x$ can be written as a convex combination of elements of $T_A(C)$ for $A = \mathrm{diag}\left[(\mathrm{sign}(x_i) \cdot d\lceil M \rceil)_{i \le d}\right] \in S$. This shows $\mathbb{R}^d \subset \bigcup_{A \in S} T_A(C)$. Therefore $\mathbb{R}^d = \bigcup_{A \in S} T_A(C)$.

Now $\mathbb{R}^d = \bigcup_{A \in S} T_A(C)$ has non empty interior, and each $T_A(C)$ is closed, so by Baire's theorem, there exists $A_0$ such that $T_{A_0}(C)$ has non empty interior. As $T_{A_0}$ is a homeomorphim, $C$ has a non empty interior too.