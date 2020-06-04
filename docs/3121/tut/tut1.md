# Binary Search

1. You are given an array S of n integers and another integer x.

(a) Describe an O(nlogn) algorithm (in the sense of the worst case perfor- mance) that determines whether or not there exist two elements in S whose sum is exactly x.

(b) Describe an algorithm that accomplishes the same task, but runs in O(n) expected (i.e., average) time.

>(a) Except for special input: empty array or invalid integer x. My solution to this question is: Firstly, use the worst case O(nlogn) sorting algorithm to sort the array, such as merge sort. 
>
>(1) for each element a in array, we calculate (x - a), then use binary search to find (x - a), so checking each element needs O(n), and binary search needs O(logn); Furthermore, if x - a = a, then we can just check the adjacent around element a; so the total complexity is merge sort plus each element binary search which is O(nlogn) + O(nlogn) = O(nlogn);
>
>(2) alternatively, we can use double pointer method. we check out the sum of the smallest element(start of array) and the largest element(end of array), if x is greater than the sum, it means the smallest element won't involve in the result, then smallest element indexs to next one; otherwise, if x is less than the sum, it means the greatest element won't involved in the result, so it also index to the next one, until we find both of them or they don't exist in the array;
>
>(b) created a hashmap, the access complexity of hashmap(hashtable) is O(1).
>
>(1) we go through the array and store each element to hashmap, then we go through the array again, check if x - a exist in the hashmap; if x - a = a, then just check if there is a copy in hashmap. O(1 * n) = O(n)

-------------

2. Given two arrays of n integers, design an algorithm that finds out in O(n log (n)) steps if the two arrays have an element in common. (Microsoft interview question)

> Two arrays denote as array A and B, the first step is to apply sorting algorithm to array A, for example, let's take merge sort (the time complexity is O(nlogn)). Then the second step is goint to index each element in array B and this takes O(n), for each element in B, we apply binary search algorithm to search if there is a same value in array A, which takes O(logn), so the total complexity is O(nlogn).
>
>Even there is no common element, the designed algorithm still takes O(nlogn).

-------------

3. Given an array A[1..100] which contains all natural numbers between 1 and 99, design an algorithm that runs in O(n) and returns the duplicated value. (Microsoft interview question)

>The designed algorithm requires hashmap(hashtable), the access complexity of hashmap(hashtable) is O(1) constant. The first step is to index each element in the array, then check if the element exists in the hashmap, if it does, then this element is a depulicated value. Otherwise, insert it into the hashmap(hashtable).

-------------

4. Assume you are given two arrays A and B, each containing n distinct positive numbers and the equation $x^8 \ − \ x^4y^4 \ = \ y^6 \ + \ x^2y^2 \ + \ 10$. Design an algorithm which runs in time O(nlogn) which finds if A contains a value for x and B contains a value for y that satisfy the equation.

> In this question, we need to clarify the relationship between x and y because we have equation $x^8 \ − \ x^4y^4 \ = \ y^6 \ + \ x^2y^2 \ + \ 10$, we can arranage this equation to: 
> $$ x^8 \ = \ x^4y^4 \ + \ y^6 \ + \ x^2y^2 \ + \ 10 $$
> from this equation we can see the right hand side the y is monotonic, this means if the right handside is greater than the left handside, so we need a smaller y, we can use binary search for this characteristic.
>
> So first we need to sort array B in O(nlogn), than we index each element in array A, and apply binary search in array B to find a element in such relationship with element in A. So the indexing plus binary search is O(nlogn).

-------------

5. You’re given an array of n integers, and must answer a series of n queries, each of the form: “how many elements of the array have value between L and R?”, where L and R are integers. Design an O(n log n) algorithm that answers all of these queries.

> The first step is to use merge sort to sort the array, which takes O(nlogn), then we apply binary search to find two important index:
>
> * First element with value no less than L;
>
> * First element with value strictly greater than R
>
> if the binary search hit L, than we need to check if there is another L value preceding this L, we need to find the first L; same rule applies to R;

-------------

6. Assume you have an array of 2n distinct integers. Find the largest and the smallest number using 3n − 2 comparisons only.



-------------

7. Assume that you have an array of $2^n$ distinct integers. Find the largest and the second largest number using only $2^n$ + n − 2 comparisons.