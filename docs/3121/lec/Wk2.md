# Wk2 Lecture recurrence

## Big Oh notation

f(n) = O(g(n)) -> there exist positive constant c and $n_0$ that $0 \leq f(n) \leq cg(n) \ for \ all \ n \geq n_0$

g(n) is asymptotic upper bound for f(n).

$f(n) = O(g(n))$ means that $f(n)$ does not grow substantially faster
than $g(n)$ because a multiple of $g(n)$ eventually dominates $f(n)$.

constants c of interest is greater than 1 (enlarge g(n)).

## Omega notation

$f(n) = Ω(g(n))$

There exists positive constants c and n0 such that 0≤cg(n)≤f(n) for all n≥n0.

In this case we say that g(n) is an asymptotic lower bound for
f (n).

f(n) = Ω(g(n)) essentially says that f(n) grows at least as fast as
g(n), because f(n) eventually dominates a multiple of g(n).

**“Theta” notation: f(n) = Θ(g(n)) if and only if f(n) = O(g(n)) and f(n) = Ω(g(n)); thus, f(n) and g(n) have the same asymptotic growth rate.**

## recurrence

$$
T(n) = 2T(\frac{n}{2}) + cn
$$

$$
T(n) = aT(\frac{n}{b}) + cn
$$

### estimate the efficiency

* no need the exact solution

* only need to find the growth rate (asymptotic behavior)

* the (approximately) size of the constants involved

This is what the master theorem provided.

### master theorem

let

* a ≥ 1 be an integer and and b > 1 an integer;

* f(n) > 0 be a non-decreasing function;

* T (n) be the solution of the recurrence T (n) = a T (n/b) + f (n);

Then

1. If $f(n) = O(n^{\log_ba−\epsilon})$ for some $\epsilon > 0$, then $T(n) = \Theta(n^{log_ba})$;

2. If $f(n) = \Theta(n^{log_ba})$, then $T(n) = \Theta(n^{log_ba} log_2 n)$;

3. If $f(n)=\Omega(n^{log_ba}+\Theta)$ for some $\Theta > 0$,and for some c < 1 and some $n_0$,

    $$
    af (n/b) \leq cf(n)
    $$
    holds for all n > n0, then $T(n) = \Theta(f(n))$;

4. If none of these conditions hold, the Master Theorem is NOT applicable.

#### remark

* for any b > 1,

$$
log_bn = log_b2 \ log_2n
$$

* Since b > 1 is constant (does not depend on n), we have for $c = log_b 2 > 0$

$$
log_bn=c \ log_2n;
$$

$$
log_2n= \frac{1}{c} \ log_bn;
$$

* Thus

$$
log_bn = \Theta(log_2n)
$$

* and also

$$
log_2n = \Theta(log_bn).
$$

So whenever we have $f = \Theta(g(n) log n)$ we do not have to specify what base the log is - all bases produce equivalent asymptotic estimates.

#### example

let T(n) = 4T(n/2) + n;

#### proof

------------------

