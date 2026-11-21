# How close must averaging start to a late Mertens crossing?

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24411643.svg)](https://doi.org/10.5281/zenodo.24411643)

This result is now maintained in [quadratic-mertens-first-crossings](https://github.com/leecrossley/quadratic-mertens-first-crossings/tree/main/results/yokoi-mertens-prescribed-crossings). This repository is archived and keeps its releases and DOI.

Assume the critical-line property for the Riemann zeta function and $L(s,\chi_d)$ for the quadratic discriminants in the theorem (field GRH). Alpöge's announced Dirichlet GRH theorem supplies this input. [Announcement](https://alpo.ge/remark.pdf) [Independent formal checks](https://math.mit.edu/~drew/grh/)

A product over the primes of a number field can stay above its expected value for a long time. Starting a weighted average early can hide its first dip. This note shows that the earliest successful start can lie at any prescribed fraction of the way to a late crossing, to any fixed relative accuracy.

The fields are $\mathbb Q(\sqrt d)$ with $d=m^2+4$ squarefree and $m$ odd. Write $S_d$ for the infimum of real $x\ge2$ where the prime-ideal Mertens product falls strictly below $e^\gamma L(1,\chi_d)\log x$, and $Y_d$ for the earliest possible start, taken as an infimum, of a negative average of the logarithmic error with bounded nonnegative decreasing weight and measure $dt/t$.

Choose $0<r\le1$ and $0<\eta\le r/4$. For every sufficiently large $D$ there is a scale $X=2^{\lfloor c(\log D)^{1/5}\rfloor}$ fixed before choosing the field. At least $\sqrt D\exp[-C(\log D)^{4/5}]$ family discriminants in $(D/2,D]$ satisfy

$$
 (r-\eta)X\le Y_d\le rX,\qquad X<S_d<(1+\eta)X.
$$

At $y=rX$, the single weight $y/t$ succeeds, and so does the finite interval ending at $(1+\eta)X$. At every start up to $(r-\eta)X$, all bounded nonnegative decreasing weights have nonnegative average, even if extended to infinity. The positive constants $c,C$ depend on $r,\eta$. Every point of $[0,1]$ occurs as a limit of $Y_d/S_d$ along waits exceeding every fixed power of $\log d$.

The construction buys a prescribed shape for the error by making small changes to the local probabilities that primes split. A fourth-moment estimate counts the actual fields that realise the shape. A polynomial deadline for **every** sufficiently large Yokoi field remains open. Daniel R. Johnston posed the original first-crossing question in 2024. [Proof](PROOF.md) · [Literature and scope](PRIOR-WORK.md) · [Problem 8](https://arxiv.org/pdf/2407.03530#page=4)

## Checking the release

Run the following in the release directory with Python 3.10 or later.

~~~sh
shasum -a 256 -c SHA256SUMS
python3 -B check.py
~~~

The Python checks enumerate finite probability spaces exactly and enclose the two profile integrals by rational rectangles. Three supporting lemmas on signed tilts, counting and integral margins are checked in Lean. The family theorem is proved in the written argument. With the pinned Lean toolchain and [Mathlib revision](https://github.com/leanprover-community/mathlib4/tree/0df444a360eaa60ab8c11dca51a86af692955474), set NOTE to this directory's absolute path, change to that Mathlib checkout and run the following.

~~~sh
lake env lean -R "$NOTE" "$NOTE/Profile.lean"
~~~

[Exact checks](evidence/check.txt) · [Lean axiom report](evidence/lean.txt) · [Upstream critical-line inputs](https://math.mit.edu/~drew/grh/)
