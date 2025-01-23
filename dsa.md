# Big O
Big O is a way to categrize your algorithm time or memory requriment.It's not meant to be exact measurement
## purpose
Tells us what data structure and  algorithm to use
## What does Big O do
Big O check as your input grows how fast does computation or memory grows
## Trick to calc Big O
look for loops
e.g.
```typescript
function print_letters(n:string){
    for(let i=0;i<n.length;i++){
        console.log(i)
    }
}
```
Big O of above is O(n) because for loop repeats the  length of string , as length of string grows so does the computation time

## Important concepts
1.Important concepts
growth is with respect to the input

2.Constants are dropped
O(2N) -> O(N) and this makes sense. That is because Big O is meant to describe the upper bound of the algorithm (the growth of the algorithm). The constant eventually becomes irrelevant.


Take the following:
N = 1, O(10N) = 10, O(N^2) = 1

N = 5, O(10N) = 50, O(N^2) = 25

N = 100, O(10N) = 1,000, O(N^2) = 10,000 // 10x bigger

N = 1000, O(10N) = 10,000, O(N^2) = 1,000,000 // 100x bigger

N = 10000, O(10N) = 100,000, O(N^2) = 100,000,000 // 1000x bigger

3.Worst case is usually we measure





