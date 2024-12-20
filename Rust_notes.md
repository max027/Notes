# Rust notes
## Ownership and borrowind
* At any given time, you can have either one mutable reference or any number of immutable references.
* References must always be valid.


## Traits
* A trait defines the functionality a particular type has and can share with other types.
* We can use traits to define shared behavior in an abstract way.
* Trait definitions are a way to group method signatures together to define a set of behaviors necessary to 
accomplish some purpose.
* Each type implementing a trait must provide its own custom behavior for the body of the method.


## Generic type
* We use generics to create definitions for items like function signatures or structs, which we can then use
with many different concrete data types


## Validating References with Lifetimes
* Rather than ensuring that a type has the behavior we want, lifetimes ensure that references are valid as long 
as we need them to be.
* The main aim of lifetimes is to prevent dangling references
* Lifetime annotations don’t change how long any of the references live.
* Rather, they describe the relationships of the lifetimes of multiple references to each other without affecting the 
lifetimes.

```Rust
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```
the above signature convery that the returned reference will be valid as long as both the parameters are valid.

* A lifetimes are named region of code that a reference must be valid for
* lifetimes are computed on bases of liveness , mean a variable is live if its current value may be used later in 
the program


## Error Handling
* Rust groups errors into two major categories: recoverable and unrecoverable errors.
    * For a recoverable error, such as a file not found error, we most likely just want  to report the problem to 
    the user and retry the operation
    * Unrecoverable errors are always symptoms of bugs, such as trying to access a location beyond the end of an array, 
     and so we want to immediately stop the program. 

* For unrecoverable we can use panic macro
* For recoverable errors we use Result enum

## Using Box<T> to Point to Data on the Heap
*  Boxes allow you to store data on the heap rather than the stack.
* When you have a type whose size can’t be known at compile time and you want to use a value of that type in a context 
 that requires an exact size
*   



## Multi threading
* A thread pool is a group of spawned threads that are waiting and ready to handle a task.
* As a reference lifetime 'static indicates that the data pointed to by the reference lives for the remaining lifetime 
  of the running program.

