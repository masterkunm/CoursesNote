# Divide and conquer

## An old puzzle: 27 coins with a one counterfeit

27 -> 9, 9, 9

9 -> 3, 3, 3

3 -> 1, 1, 1

## m users rank the same set of n movies

count the inversion

tweak the merge sort O(nlogn)

## how to add two numbers

linear time

## how to multiply two numbers

divide and conquer method:

$$
A = A_1 2^\frac{n}{2} + A_0
$$

$$
B = B_1 2^\frac{n}{2} + B_0
$$

$$
AB = A_1B_12^n + (A_1B_0 + A_0B_1)2^\frac{n}{2} + A_0B_0 \ \ \ ---O(n^2)
$$

### The Karatsuba trick

$$
AB = A_1B_12^n + ((A_1+A_0)(B_1 + B_0) - A_1B_1 - A_0B_0)2^\frac{n}{2} + A_0B_0 \ \ \ ---O(n^{1.58})
$$

## strassen 's algorithm (also use Karatsuba trick)




