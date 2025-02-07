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


# Queue
A Queue is specific implementation of linkedlist

* Queue operate on principle of first in first out , that mean element that is inserted first will be first to get deleted
* In Queue we add at tail and remove at head

## javascript code for Queue
```javascript
class Queue {
    constructor() {
        this.items = {}
        this.frontIndex = 0
        this.backIndex = 0
    }
}
```

# Stack

Just like queue stack are specific implementation of linkedlist

* Stack work on principle of last in first out , that mean element that was inserted last will be first to removed
* In stack we add and remove at head

# Arrays vs linkedlist
* Traversal : In array you have indices access while in linkedlist you dont.That means in linkedlist you have to traverse one node at time to get specific node
* Insertion and Deletion: In linkedlist Insertion and Deletion is constant time, you only assign and reassign links.While in array you dont insert or delete because of fixed size,you only shift and unshift.


# Recursion
A function that keeps calling itself until it reach a base condition

Recursion can be broken down into 2 steps 
1. base case
2. recurse

A good Base case is important for recursion, othervise recursion will exceed the stack limits

## Example of Recursion in javascript
```javascript
function add(n){
    if(n===1){
        return 1 
    }
    return n+add(n-1)
}
```

# Divide and conqure
Divide and Conquer Algorithm is a problem-solving technique used to solve problems by dividing the main problem into subproblems, solving them individually and then merging them to find solution to the original problem

# Quick sort
In quick sort we first select pivot and put element less than or equal to pivot on left side and element greater than on right side
then we split our array into two left side of pivot and right side of pivot and repeat entire process.


# Tree
trees are a type of data structure used to represent hierarchical relationships
* Root
    * The top node of the tree. It is the starting point of traversal.
* Leaf
    *  A node that has no children.
* Height
    * The length of the longest path from a node to a leaf node.

# Traversal
* pre order
* post order
* in order
