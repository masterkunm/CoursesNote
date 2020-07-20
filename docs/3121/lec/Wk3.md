# Wk3 lecture

## Integer multiplication

### the karatsuba trick -> master theorem

### generalizing karatsuba's algorithm

k = n/3

slicing into 3 pieces

use:

$$
P_A(x) = A_2x^2 + A_1x + A_0;
$$
$$
P_B(x) = B_2x^2 + B_1x + B_0;
$$

rather:

$$
A = A_22^{2k} + A_12^k + A_0
$$
$$
B = B_22^{2k} + B_12^k + B_0
$$

and:

$$
A = P_A(2^k), B = P_B(2^k)
$$