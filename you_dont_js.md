# You dont know js

# Types and Grammer
## Built in types
*  null
*  undefined
*  boolean
*  number
*  string
*  object
*  symbol—added in ES6!

* a function is referred to as a “callable object” an object that has an internal [[Call]] property that allows it to be
invoked.

* In JavaScript, variables don’t have types values have types

## Values
### Arrays
* JavaScript arrays are just containers for any type of value, from string to number to object to even another array 

* if a string value intended as a key can be coerced to a standard base-10 number, then it is assumed that you wanted to use it as a 
number index rather than as a string key!

```javascript
var a = [ ];
a["13"] = 42;
a.length; // 14
```
*  Use objects for holding values in keys/properties, and save arrays for strictly numerically indexed values.

### Strings
* JavaScript strings are immutable

### Numbers
* JavaScript has just one numeric type: number. This type includes both “integer” values and fractional decimal numbers

### Undefined
* undefined hasn’t had a value yet.
* null had a value and doesn’t anymore
* null is a special keyword, not an identifier

### Values and References
* Simple values (aka scalar primitives) are always assigned/passed by value-copy: null, undefined, string, number, boolean, 
    and ES6’s symbol

    * Compound values—objects (including arrays, and all boxed object wrappers) and functions—always create a copy of
    the reference on assignment or passing.

## Internal [[Class]]
* Values that are typeof of "object" (such as an array) are additionally tagged with an internal [[Class]] property (think of this more
as an internal classification rather than related to classes from traditional class-oriented coding)
* This property cannot be accessed directly, but can generally can be revealed indirectly by borrowing the default Object.prototype.toString(..) method called against the value.
```javascript
    Object.prototype.toString.call( [1,2,3] );
    // "[object Array]"
    Object.prototype.toString.call( /regex-literal/i );
    // "[object RegExp]"
    Object.prototype.toString.call( null );
    // "[object Null]"
    Object.prototype.toString.call( undefined );
    // "[object Undefined]"
```
* You’ll note that there are no Null() or Undefined() native con‐ structors, but nevertheless "Null" and "Undefined" are the internal [[Class]] values exposed.

## Boxing Wrappers
* Primitive values don’t have properties or methods, so to access .length or .toString() you need an object wrapper around the value
* using the boxed object wrapper directly is usually discouraged
* There’s practically no reason to ever use the new Object() constructor form, especially since it forces you to add properties one by one
instead of many at once in the object literal form.

## Object Wrapper Gotchas
```javascript
    var a = new Boolean( false );
    if (!a) {
        console.log( "Oops" ); // never runs
    }
```
* The problem is that you’ve created an object wrapper around the false value, but objects themselves are “truthy”
## Unboxing
* If you have an object wrapper and you want to get the underlying primitive value out, you can use the valueOf() method
```javascript
var a = new String( "abc" );
var b = new Number( 42 );
var c = new Boolean( true );
a.valueOf(); // "abc"
b.valueOf(); // 42
c.valueOf(); // true
```
## Native Prototypes
* Each of the built-in native constructors has its own .prototype object — Array.prototype, String.prototype, etc.
These objects contain behavior unique to their particular object subtype.
Here’s a list of the most commonly used natives:
    • String()
    • Number()
    • Boolean()
    • Array()
    • Object()
    • Function()
    • RegExp()
    • Date()
• Error()
    • Symbol()—added in ES6!
    * these natives are actually built-in functions
    * The result of the constructor form of value creation (new String("abc")) is an object wrapper around the primitive ("abc")
    value.
    ```javascript
    var a = new String( "abc" );
    typeof a; // "object" ... not "String"

    ```

* JavaScript provides object wrappers around primitive values, known as natives (String, Number, Boolean, etc)
    * These object wrappers give the values access to behaviors appropriate for each object sub‐ type (String#trim() and Array#concat(..)).

# Coercion
Converting a value from one type to another is often called “type casting,” when done explicitly, and “coercion” when done implicitly
* When any non-string value is coerced to a string representation, the conversion is handled by the ToString abstract operation in section 9.8 of the specification.
* For most simple values, JSON stringification behaves basically the same as toString() conversions, except that the serialization result
is always a string:
```javascript
    JSON.stringify( 42 ); // "42"
    JSON.stringify( "42" ); // ""42"" (a string with a
                            // quoted string value in it)
    JSON.stringify( null ); // "null"
    JSON.stringify( true ); // "true"

```
 The JSON.stringify(..) utility will automatically omit undefined, function, and symbol values when it comes across them
```javascript
    JSON.stringify( undefined ); // undefined
    JSON.stringify( function(){} ); // undefined
    JSON.stringify(
            [1,undefined,function(){},4]
            ); // "[1,null,null,4]"
    JSON.stringify(
            { a:2, b:function(){} }
            ); // "{"a":2}"

```
Arrays have an overridden default toString() that stringifies as the (string) concatenation of all its values (each stringified themselves), with ","
## ToNumber
If any non-number value is used in a way that requires it to be a number, such as a mathematical operation, the ES5 spec defines the ToNumber abstract operation in section 9.3.

* If valueOf() is available and it returns a primitive value, that value is used for the coercion. 
* If not, toString() will provide the value for the coercion, if present.
* If neither operation can provide a primitive value, a TypeError is thrown.
```javascript
var a = {
 valueOf: function(){
 return "42";
 }
};
var b = {
 toString: function(){
 return "42";
 }
};

Number( a ); // 42
Number( b ); // 42
```

## ToBoolean
### Falsy values
* undefined
* null
* false
* +0, -0, and NaN
*  ""

# Explicit Coercion
Explicit coercion refers to type conversions that are obvious and explicit
* The ~ operator first “coerces” to a 32-bit number value, and then performs a bitwise negation (flipping each bit’s parity).

## Explicitly: Parsing Numeric Strings
Using parseInt on non-string value,If you pass a non-string, the value you pass will automatically be coerced to a string first , which would
clearly be a kind of hidden implicit coercion. It’s a really bad idea to rely upon such behavior in your program, so never use par
seInt(..) with a non-string value.
