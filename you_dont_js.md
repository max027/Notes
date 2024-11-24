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


