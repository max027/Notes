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


## Enums
enums give you a way of saying a value is one of a possible set of values. For example, we may want to say that Rectangle is one of a set of possible shapes that also includes Circle and Triangle.
```rust
enum WebEvent {
    // An `enum` variant may either be `unit-like`,
    PageLoad,
    PageUnload,
    // like tuple structs,
    KeyPress(char),
    Paste(String),
    // or c-like structures.
    Click { x: i64, y: i64 },
}

```

## Vectors
Vectors allow you to store more than one value in a single data structure that puts all the values next to each other in memory. Vectors can only store values of the same type. They are useful when you have a list of items, such as the lines of text in a file or the prices of items in a shopping cart.
```rust
let v: Vec<i32> = Vec::new();

let v = vec![1, 2, 3];
```

## Structs
There are three types of structures ("structs") that can be created using the struct keyword:
* Tuple structs, which are, basically, named tuples.
* The classic C structs
* Unit structs, which are field-less, are useful for generics.
```rust
// An attribute to hide warnings for unused code.
#![allow(dead_code)]

#[derive(Debug)]
struct Person {
    name: String,
    age: u8,
}

// A unit struct
struct Unit;

// A tuple struct
struct Pair(i32, f32);


```

## Result Enums
```rust
enum Result<T, E> {
    Ok(T),   // Success case (contains a value of type T)
    Err(E),  // Error case (contains an error of type E)
}
```
### Propagating Errors
When a function’s implementation calls something that might fail, instead of handling the error within the function itself you can return the error to the calling code so that it can decide what to do. This is known as propagating the error and gives more control to the calling code, where there might be more information or logic that dictates how the error should be handled than what you have available in the context of your code.
### Where The ? Operator Can Be Used
The ? operator can only be used in functions whose return type is compatible with the value the ? is used on. This is because the ? operator is defined to perform an early return of a value out of the function,




## Generic type
* We use generics to create definitions for items like function signatures or structs, which we can then use
with many different concrete data types
```rust
//function
fn largest<T:std::cmp::partialOrd>(list: &[T]) -> &T {
    let mut largest = &list[0];

    for item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}

struct Point<T> {
    x: T,
    y: T,
}

enum Option<T> {
    Some(T),
    None,
}

impl<T> Point<T> {
    fn x(&self) -> &T {
        &self.x
    }
}
```

## Traits
A trait defines the functionality a particular type has and can share with other types. We can use traits to define shared behavior in an abstract way. We can use trait bounds to specify that a generic type can be any type that has certain behavior.
```rust
pub trait Summary {
    fn summarize(&self) -> String;
}

impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{}, by {} ({})", self.headline, self.author, self.location)
    }
}
```

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

