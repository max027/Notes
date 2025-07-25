Competitive programming combines two topics: (1) the design of algorithms and (2) the implementation of algorithms.
* The design of algorithms consists of problem solving and mathematical thinking. 
* The implementation of algorithms requires good programming skills.

# Time complexity
The time complexity of an algorithm estimates how much time the algorithm will use for some input.
## Calculation rules
The time complexity of an algorithm is denoted O(· · · ) where the three dots represent some function. Usually, the variable n denotes the input size

### Loops
A common reason why an algorithm is slow is that it contains many loops that go through the input.  The more nested loops the algorithm contains, the slower it is.
* If there are k nested loops, the time complexity is O(nk)

### Phases
If the algorithm consists of consecutive phases, the total time complexity is the largest time complexity of a single phase.
The reason for this is that the slowest phase is usually the bottleneck of the code.
For example, the following code consists of three phases with time complexities
O(n), O(n2) and O(n). Thus, the total time complexity is O(n2)

* An algorithm is polynomial if its time complexity is at most O(nk) where k is a constant.

# Sorting 
## Inversions
a pair of array elements (array[a], array[b]) such that a < b and array[a] > array[b], i.e., the elements are in the wrong order.
*  An array is completely sorted when there are no inversions.

## merge sort
Merge sort sorts a subarray array[a . . . b] as follows:
1. If a = b, do not do anything, because the subarray is already sorted.
2. Calculate the position of the middle element: k = b(a + b)/2.
3. Recursively sort the subarray array[a . . . k].
4. Recursively sort the subarray array[k + 1 . . . b]
5. Merge the sorted subarrays array[a . . . k] and array[k + 1 . . . b] into a sorted subarray array[a . . . b].

## counting sort
The lower bound n log n does not apply to algorithms that do not compare array elements but use some other information.
An example of such an algorithm is counting sort that sorts an array in O(n) time assuming that every element in the array is an integer between 0 . . . c and c = O(n). 



# Math


# Bitwise operator trick

## even and odd
```
x&1==1
```

## is power of 2
```
x&(x-1)==0
```
does not work for x==0

## multiply or divide by 2^k
eg 10/2 where 2 is 2^1
```
x/2  ---- x>>1
x/4 ----- x>>2
x/2^k --- x>>k

x*2^k ---- x<<k
```

## swap two variable without temp variable
```
x=x ^ y
y=x ^ y
x=x ^ y
```
## 
```
if x==a
    then x=b
if x==b
    then x=a

x= a ^ b ^ a
```
