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

The operator **+** is overloaded to perform either numeric addition or string concatenation

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

- Bad Part!
**Silent coercions can make debugging a broken program particularly frustrating, since they cover up errors and make them harder to diagnose** 

