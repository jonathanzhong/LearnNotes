#Effective Javascript Notes

### JavaScript's Floating-point Numbers

All numbers in JavaScript are double-precision floating-point numbers, that is the 64-bit encoding of numbers by the IEEE 754 standard - commonly known as "doubles"

Bitwise operator: converting inputs -> integers -> performance operations -> standard JavaScript floating-point numbers.

- Things to remember
 * JavaScript numbers are double-precision floating-point numbers.
 * Intergers in JS are just a subset of doubles rather than a separate datatype.
 * Bitwise operator treat numbers as if they were 32-bit signed integers.
 * Be aware of **limitations of precisions** in floating-point arithmetic.


### Implicit Coercions

Dynamically typed languages will allow program to run like `3 + true`, while statically typed languages don't. 

There are a handful of cases in JavaScript where providing the wrong type produces an immediate erro, such as calling a `nonfunction` or attempting to `select a property of null`.

The operator **+** is overloaded to perform either **numeric addition** or **string concatenation**

    2 + "3"; //"23"
    1 + 2 + "3"; //"33"
    (1 + 2) + "3"; //"33"
    1 + "2" + 3; //"123"

But coercions can also hide errors. A variable that turns out to be **null** will not fail in an arithmetic calculation, but silently convert to 0; an undefined variable will convert to the special floating-point value **NaN**. Rather than throwing an exception, these coercions cause the calculation to continue with often confusing and unpredictable results.

Not able to test **NaN** value: 1. JavaScript follows the IEEE floating-point standard's headscratching requirement that NaN be treated as unequal to itself. 2. The standard **isNaN** library function is not reliable because it comes with its own implicit coercion, converting its argument to a number before testing the value.

Since **NaN** is the only JavaScript value that is treated as unequal to itself.

    var a = NaN;
    a !== a;  // True

Hence we can check it for equality to itself, the result of `true` indicates that `a` is NaN!

BAD PART!
**Silent coercions can make debugging a broken program particularly frustrating, since they cover up errors and make them harder to diagnose** 

Objects -> String: **toString**;
Objects -> Number: **valueOf**;

*falsy* Value: false, 0, -0, "", NaN, null and undefined.

```
function point(x, y) {
    if (!x) {
        x = 320;
    }

 if (!y) {
        y = 240;
    }
    return { x: x, y: y };
}

point(0, 0);// {x: 320, y: 240}

The more precise way to check for *undefined* is to use *typeof*:
“function point(x, y) {
    if (typeof x === "undefined") {
        x = 320;
    }
    if (typeof y === "undefined") {
        y = 240;
    }
    return { x: x, y: y };
}”
This version of point correctly distinguishes between 0 and undefined.
```


- Things to Remember:
    * Type errors can be silently hidden by implicit coercions.
    * The + operator is overloaded to do addition or string concatenation depending on its argument types.
    * Objects are coerced to numbers via *value of*  and to string via *toString*.
    * Objects with *valueOf* methods should implement a *toString* method that provides a string representation of the number produced by *valueOf*.
    * Use *typeof* or comparison to *undefined* rather than truthiness to test for undefined values.



### Prefer Primitives to Object Wrappers

In addition to objects, JavaScript has five types of primitive values: *booleans*, *numbers*, *strings*, *null*, and *undefiend*. (**This is one of the interview question I met.**)

`var s = new String ("Hello");` This is a string object, but behaves similarly to the string value it wraps.

- Things to Remember:
  * Object wrappers for primitive types do not have the same behavior as their primitive values when compared for equility.
  * Getting and setting properties on primitives implicity creats object wrappers.


### Avoid using == with Mixed Types

Using strict equality ("===") is a good way to make it clear to readers that there is no conversion involved in the comparison. Otherwise, you require readers to recall the exact coercion rules to decipher your code's behavior.

```
var date = new Date("1999/12/31")
date == "1999/12/31"; //false
```

This particular example failse because converting a Data object to a string produces a different formate than the one used in the example.

A better policy is to make the conversion explicit with custom application logic and use the strict equality operator:

```
function toYMD(date) {
    var y = date.getYear() + 1900, // year is 1900-indexed
        m = date.getMonth() + 1,   // month is 0-indexed
        d = date.getDate();
    return y
         + "/" + (m < 10 ? "0" + m : m)
         + "/" + (d < 10 ? "0" + d : d);
}
toYMD(date) === "1999/12/31"; // true
```


- Things to Remember:
    * The == operator applies a confusing set implicit coercions then its arguments are of different types.
    * Use === to make it clear to your readers that your comparison does not involve any implicit coercions.
    * Use your own explicit coercions when comparing value of different types to make your program's behavior clearer.


### Learning the limits of Semicolon Insertion

one of JavaScript's conveniences is the ability to leave off statement-terminating semiconlons.

rules of semicolon insertion:

1. Semiconlons are only inserted before a } token, after one or more newlines, or at the end of the program input.(leave out semicolons at the end of a lin, block, or program.)
2. Semicolons are only ever inserted when the next input token cannot be parsed. (watch out for 5 problematic characters: (, [, +, - and /; JavaScript allows comma-separated expressions, which evaluate from left to right and return the value of their last subexpression)
3. 

### Think of Strings As Sequences of 16-bit Code Units

*理解无能，再回头看吧* 

## Variable Scope
JavaScript's core scoping rules are simple, well designed and incredibly powerful.
### Minimize use of the Global Object
Downside of Global variables: the posibility of accidental name collisions; against modularity, lead to unnecessary coupling between separate components of a program.

In web browsers, the global object is also bound to the global *window* variable.

－ Things to Remember: 
  * Avoid declaring global variables.
  * Declare variables as locally as possible.
  * Avoid adding properties to the global object.
  * Use the global object for platform feature detection.

### Always Declare Local Variables.
undeclared local variable -> *unintentional* global variable
use *lint* tools for bad style or potential bugs, and often feature the ability to report uses of unbound variables.

### Avoid *with*

### Get Comfortable with Closures

Understanding closures only requires learning **three essential facts**.

The first fact is that JavaScript allows you to refer to variables that were defined outside of the current function(use **return** the variable).

The second fact is that functions can refer to variables defined in outer functions even *after* those outer functions have returned!  

The third fact is that they can update the values of outer variables.


- Things to Remember
    * Functions can refer to variables defined in outer scopes.
    * Closures can outlive the function that creats them.
    * Closures internally store references to their outer variables, and can both read and update their stored variables.

### Understand Variable Hoisting(提前)

JavaScript supports *lexical scoping* but not *block scoping*

the variable declaration will be hoisted to the beginning of lexical scope.

- Things to Remember:
  *  Variable declarations within a block are implicitly hoisted to the top of their enclosing function.
  *  Redeclarations of a variable are treated as a signle variable.
  *  Consider manually hoisting local variable declarations to avoid confusion.(place all var declarations at the top of their functions.)


### Use Immediately Invoked Function Expressions to Create Local Scopes



