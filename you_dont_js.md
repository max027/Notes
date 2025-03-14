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

# Implicit Coercion
Implicit coercion refers to type conversions that are hidden, with nonobvious side effects that implicitly occur from other actions.

## Implicitly: Strings <--> Numbers
* You can coerce a number to a string simply by “adding” the number and the "" empty string:
```javascript
var a = 42;
var b = a + "";
b; // "42"
```

## Implicitly: * --> Boolean
1. The test expression in an if (..) statement
2. The test expression (second clause) in a for ( .. ; .. ; .. )
header
3. The test expression in while (..) and do..while(..) loops
4. The test expression (first clause) in ? : ternary expressions
5. The lefthand operand (which serves as a test expression—see
below!) to the || (“logical or”) and && (“logical and”) operators

Any value used in these contexts that is not already a boolean will be implicitly coerced to a boolean using the rules of the ToBoolean
abstract operation

Quoting the ES5 spec from section 11.11:

***The value produced by a && or || operator is not necessarily of type
Boolean. The value produced will always be the value of one of the
two operand expressions.*** 

```javascript
var a = 42;
var b = "abc";
var c = null;
a || b; // 42
a && b; // "abc"
c || b; // "abc"
c && b; // null
```
For the || operator, if the test is true, the || expression results in the value of the first operand (a or c). If the test is false, the || expression results in the value of the second operand (b).

Inversely, for the && operator, if the test is true, the && expression results in the value of the second operand (b). If the test is false, the && expression results in the value of the first operand (a or c).

## Loose Equals Versus Strict Equals
== allows coercion in the equality comparison and === disallows coercion.


# Grammer
Every expression in JS can be evaluated down to a single, specific value result.
```javascript
var a = 3 * 6;
var b = a;
b;
```
any regular { .. } block has a completion value of the completion value of its last contained statement/expression.
```javascript
var b;
if (true) {
 b = 4 + 38;
}
```
If you typed that into your console/REPL, you’d probably see 42 reported, since 42 is the completion value of the if block, which took on the completion value of its last expression statement b = 4 + 38.
## labeled statement
```javascript
{
 foo: bar()
}
```
foo is a label for the statement bar() (that has omitted its trailing ;

```javascript
// `foo` labeled-loop
foo: for (var i=0; i<4; i++) {
 for (var j=0; j<4; j++) {
 // whenever the loops meet, continue outer loop
 if (j == i) {
 // jump to the next iteration of
 // the `foo` labeled-loop
 continue foo;
 }
 // skip odd multiples
 if ((j * i) % 2 == 1) {
 // normal (nonlabeled) `continue` of inner loop
 continue;
 }
 console.log( i, j );
 }
}
// 1 0
// 2 0
// 2 1
// 3 0
// 3 2
```
continue foo does not mean “go to the foo labeled position to continue,” but rather, “continue the loop that is labeled foo with its next iteration.” So, it’s not really an arbitrary goto.
A label can apply to a nonloop block, but only break can reference such a nonloop label
You can do a labeled break ___ out of any labeled block, but you cannot continue ___ a nonloop label, nor can you do a nonlabeled break out of a block

```javascript
[] + {}; // "[object Object]"
{} + []; // 0
```
On the first line, {} appears in the + operator’s expression, and is therefore interpreted as an actual value (an empty object). [] is coerced to "" and thus {} is coerced to a string value as well: "[object Object]".
But on the second line, {} is interpreted as a standalone {} empty block (which does nothing). Blocks don’t need semicolons to terminate them, so the lack of one here isn’t a problem. Finally, + [] is an
expression that explicitly coerces the [] to a number, which is the 0 value.

## else if and optional blocks
It’s a common misconception that JavaScript has an else if clause,
because you can do
```javascript
if (a) {
 // ..
}
else if (b) {
 // ..
}
else {
 // ..
}
```
But there’s a hidden characteristic of the JS grammar here: there is no else if. But if and else statements are allowed to omit the { }
around their attached block if they only contain a single statement.

```javascript
if (a) {
 // ..
}
else {
 if (b) {
 // ..
 }
 else {
 // ..
 }
}
```
