---
jupytext:
  formats: ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.10.3
kernelspec:
  display_name: Python 3.9.4 64-bit
  language: python
  name: python3
---

# Errata to "An Introduction to Ramsey Theory"


*If you think you found an error that is not listed below, please contact me (<a href="mailto:jan.reimann@psu.edu">jan.reimann@psu.edu</a>).*

## Page 24, Proof of Theorem 1.24

Not strictly an error, but to conclude that $\binom{2k-2}{k-1}$ is a better bound than $2^{2k}$, one can simply observe that $\binom{2k-2}{k-1}$ is a coefficient in the binomial expansion of 

$$
    (1+1)^{2k-2} = 2^{2k-2}
$$

and hence must be quite smaller than $2^{2k}$. No need to use Stirling's formula here.

[*Thanks to **Paul Epstein** for this observation.*]

## Pages 31-34, Proof of Turán's Theorem

The proof given here only works in the case where $k-1$ divides $N$, in which case we end up with a (perfectly balanced) $(k-1)$-partite graph. For the general case, the construction will yield a graph $K_{n_1, \dots, n_{k-1}}$ with $n_{k-1}=\mid T\mid$. It remains to show that any such graph also obeys the Turán bound 

$$
    \left ( 1- \dfrac{1}{k-1} \right) \frac{N}{2}. 
$$

By the "swapping" argument on page 32, it is enough to verify this for Turán graphs (i.e. where $\mid n_i - n_j\mid \leq 1$), and we leave this as an exercise.

[*Thanks to **Paul Epstein** for pointing this out.*]


## Page 44, A different proof of Ramsey's Theorem

*The inductive argument as laid out in the text, is not quite clear. Below is a better version. Thanks to **Paul Epstein**  and **Isaac Goldbring** for pointing this out (independently).*

Call an $r$-coloring $c:[X]^p \to \{0,\dots, r-1\}$  *good* if for any $x,y \in [X]^p$, if $\min x = \min y$, then $c(x) = c(y)$, that is, if two $p$-sets have the same beginning, then they have the same color. 

*Claim I:* Let $p, r$ be positive integers. The following statement are equivalent.

1. For all $k \geq 1$, $R(p,k,r)$ exists.
2. For all $k\geq 1$, there exists an integer $N$ such that if $\mid X\mid  \geq N$ and $c:[X]^p \to \{0,\dots, r-1\}$ is an $r$-coloring of the $p$-element subsets of $X$, then there exists a subset $Y$ of $X$ of size $k$ such that $c$ is good on $[Y]^p$.

We use the following notation for a number $N$ as in (2):

$$
N \; \overset{\text{good}}{\longrightarrow} (k)^p_r.
$$

The direction (1) $\Rightarrow$ (2) is clear, since every monochromatic coloring is a good coloring. 

To prove (2) $\Rightarrow$ (1), given $k \geq 1$, choose $N$ large enough so that 

$$
N \; \overset{\text{good}}{\longrightarrow} (r(k-1)+1)^p_r.
$$

This is possible since we assume that (2) holds for *all* $k$.
We claim that for this $N$, 

$$
N \; \longrightarrow (k)^p_r.
$$

So, let $c$ be an $r$-coloring of $[N]^p$. By choice of $N$, there exists a set $Y \subseteq [N]$ of size $r(k-1)+1$ such that $c$ is good on $[Y]^p$. Now define a new coloring $c^*: Y \to \{0,\dots, r-1\}$ be letting

$$
c^*(y) = \text{the color of any $p$-set in $[Y]^p$ in which $y$ is the least element}
$$
for any $y \leq r(k-1)-p+2$ (and $c^*(y) = 0$ otherwise, when $y$ cannot be the least element in a $p$-set). 
This coloring is well-defined due to the goodness of $c$ on $[Y]^p$.

By the pigeonhole principle, since $Y$ is of size $r(k-1)+1$, there must exist a subset $Z \subseteq Y$ of size $k$ on which $c^*$ is monochromatic. This in turn implies, using the fact that $c$ is good on $[Z]^p$, that $c$ is monochromatic on $[Z]^p$.

*Claim 2*: For every $k,p,r \geq 1$, there exists an $N$ such that 
$$
N \; \overset{\text{good}}{\longrightarrow} (k)^p_r.
$$

Claim 2 is proved by *double induction* on $k$ and $p$ ($r$ remains arbitrary but fixed throughout). We already know the claim holds for $k = p = 1$. 

Let us assume Claim 2 holds for $p-1$ and for *all* $j$. Moreover, we assume that Claim 2 holds for $p$ and for all $j \leq k$. So let us choose $N$ such that
$$
    N \; \overset{\text{good}}{\longrightarrow} (k)^p_r.
$$

Because we already verified Claim 1 we can use the fact that $R(p-1,j,r)$ exists for *all* $j$.
In particular, we can choose $M$ such that
$$
    M \longrightarrow (N)^{p-1}_r.
$$
We claim that 
$$
    M+1\overset{\text{good}}{\longrightarrow} (k+1)^p_r.
$$

Let $c$ be an $r$-coloring of $[M+1]^p$. We define an $r$-coloring 
$c^{-}$ on $[\{2,\dots, M+1\}]^{p-1}$ by letting 
$$
    c^-(x_1, \dots, x_{p-1}) = c(1, x_1,\dots, x_{p-1}).
$$
By choice of $M$, there exists a subset $Y \subseteq \{2, \dots, M+1\}$ of size $N$ such that $c^-$ is monochromatic on $[Y]^{p-1}$, which in turn means that $c$ is good for any $p$-set of $\{1\} \cup Y$ starting with $1$.

By choice of $N$, there exists a subset $Z \subseteq Y$ of size $k$ such that $c$ is good on $[Z]^{p}$. It follows that $c$ is good on $[\{1\} \cup Z]^{p}$, as desired.

Claim 1 and 2 together prove the general Ramsey theorem. 



## Page 54, proof of Theorem 2.12


*The proof as written does not work, as it is not guaranteed that the $n_i$ will go to infinity. Thanks to __Shamil Asgarli__ for pointing this out, and for suggesting the following proof.*


We simultaneously define, inductively, an infinite path $t \in [T]$ and a subsequence $s_{n_k}$ such that $s_{n_k} \to t$ for $k \to \infty$. 

We put $t^0 = r$ and $s_{n_0} = s_0$. Note that the set 

$$
    S_0 = \{ m \colon s_m^0 = t^0 \}
$$

is infinite (every sequence passes through the root node).


Now assume we have defined $t^0 < \ldots < t^k$, where each $t^i$ is in $T$ and an immediate predecessor of $t^{i+1}$, and $s_{n_0}, \ldots, s_{n_k} $ such that the set
$$    
    S_k = \{ m \colon s_m^0 = t^0, \ldots, s_m^k = t^k \}
$$
is infinite. Note that all sequences in $S_k$ have distance at most
$2^{-k}$ from each other in the path metric, since they all have the same first $k$
elements. $S_k$ is infinite and $T$ is finitely branching, hence by the
pigeonhole principle we can
find an immediate successor $t^{k+1} \in T$ of $t^k$ such that 
$$
    S_{k+1} = \{ m \colon s_m^0 = t^0, \ldots, s_m^k = t^k, s_m^{k+1} = t^{k+1}  \}
$$
is infinite. Let $n_{k+1}$ be the smallest number $m \in S_{k+1}$ that is greater than $n_k$.

Since all $t^k$ are on $T$, they define an infinite path 
$$
    t = t^0 \, t^1\, t^2 \, \ldots  \in [T].
$$

By definition of $t^k$, $d(t, s_{n_k}) \leq 2^{-k}$, and thus $(s_{n_k})$ converges to $t$ in the path metric.


## Page 75, line 20 

*The sentence starting with "Pick
the $\prec$-least element $\ldots$'' should read:* 

"Pick the $\prec$-least element $x_{\alpha_1}$ of $Z_1$ (which must
exist since $\prec$ is a well-ordering) and observe that $\{y
\in Z_1: c(x_\{\alpha_1\},y) = \text{red} \}$ is again
uncountable." 

*Thanks to **Shamil Asgarli** for catching
this.*


## Page 158, big formula (formal statement of Ramsey's theorem)

_The last line of the formula is incorrect -- we need to check __each__ entry in the argument of the function whether it is an element of the set coded by $z$. The line should read as follows:_

$$
    \forall m \leq l \: ( \, \forall s \leq p \exists i \leq k (\operatorname{decode}(\operatorname{arg}(f,m),s)=\operatorname{decode}(z,i)) \; \Rightarrow \; \operatorname{val}(f,m)=j \,)
$$ 

[Thanks to __Vineet Gupta__ and __Adnan Aziz__ for pointing this out.]


## Page 180, proof of Proposition 4.46:

The transition from the formula 
$$
  \mathcal{N} \models \exists x_1 \forall x_2 \ldots \exists x_n \: \psi(a, \vec{c}, \vec{x})
$$
to the $\Delta_0$ formula using "meta"-quantifiers needs further justification. In particular, it does _not_ follow inductively by simply applying logical equivalences. Instead, the property of indiscernibles has to be invoked at this step already.

[Click here](http://personal.psu.edu/jsr25/Ramsey_Book_4_5_patch.pdf) for an improved writeup of the argument (covering the remainder of the proof of Proposition 4.46)

Thanks to **Michael Weiss** for bringing up this important issue. Michael has a blog [diagonalargument.com](https://diagonalargument.com) I recommend. Among other entries, there is a series of "conversations" with John Baez about non-standard models of PA. [Here](https://diagonalargument.com/2019/05/06/non-standard-models-of-arithmetic-1/) is the first entry. Check it out! 

Finally, for the connoisseurs, Michael has provided a proof of the above transition that does not use indiscernibility: [PDF file](http://personal.psu.edu/jsr25/michael_weiss_patch.pdf)

## Page 182, Definition 4.48

_The definition should read:_ 

Let $X \subseteq \mathbb{N}$, $n \geq 1$, and suppose $f: [X]^n \to \mathbb{N}$. A set $M \subseteq X$ with $\mid M\mid  > n$ is **min-homogeneous** if for every $s, t \in [M]^n$, 
$$    
    \min s = \min t \; \Rightarrow \; f(s) = f(t).
$$

[Thanks to __Vineet Gupta__ and __Adnan Aziz__]

## Page 186/187, proof of Lemma 4.52

At several places $[W]^{n+1}$ should be $[Y]^{n+1}$ instead: page 186, lines 3, 6, last line of the second last paragraph, and page 187, line 2.   

[Thanks to __Vineet Gupta__ and __Adnan Aziz__]
