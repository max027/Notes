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

# Search
## Linear Search
In linear search we scan our dataset one element at a time , and check if the given element is our target
### Time complexity
Linear O(N) - because at worst case we scan our entire dataset and we dont find the given target
### Javascript code 
```Javascript
function Linear(arr,target){
    for(let i=0;i<arr.length;i++){
        if(arr[i]===target){
            return true
        }
    }
    return false
}
```


## Binary Search
It only work on sorted dataset.Instead of scanning entire dataset one element at time, we check middle element, if the middle element is our target then we found our target.
If not then we check wheather our target element is smaller than middle then we check our left portion of dataset,else we check right portion of dataset

### Time complexity
O(log n) - because we check middle element then we half our dataset. 

### Javascript code 
```Javascript
function Binary_search(arr,target){
    let l=0;
    let r=Math.floor(arr.length-1)
    while (l<r){
        let mid=(l+(r-l))/2
        if(arr[mid]===target){
            return true
        }else if(arr[mid]>target){
            r=mid
        }else{
            l=mid+1
        }
    }
    return false
}
```


# Arrays
Arrays are fixed sized collection of same type of element arrange continiguous in manner
## properties
Arrays cant grows or shrink because They are fixed size, continiguous memory chunks

# Linked List
## Disadvantage of arrays
* Insertion
* Deletion
* Ungrowable

Linkedlist is also called Node based datastructure.

Node contain two thing 
1. Value
2. Reference to another node

Head is first Node in linked list
Tail is last Node in linkedlist
Insertion and Deletion can be very fast in linkedlist
In order to access the element you have to traverse the list because there are no index

## Singly Linkedlist
In sligly linkedlist we have a node containing value and reference to next node.In sligly linkedlist you can only traverse forward not in both direction.
## javascript code for singly linkedlist 
```javascript
class Node{
    constructor(element){
        this.element=element
        this.next=null
    }
}
```

## Doubly Linkedlist
In Doubly linkedlist we have a node containing value and reference to next and previous node.In Doubly linkedlist you can traverse in both direction
## javascript code for doubly linkedlist 
```javascript
class Node{
    constructor(element){
        this.element=element
        this.next=null
        this.prev=null
    }
}
```

Operations on linkedlist
1. Insertion at head or tail
2. Insertion at middle
3. Deletion at head or tail
4. Deletion at middle



