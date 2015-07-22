# JavaScript Interview Questions

- How would you compare two objects in JavaScript?
  ```
  function isEqual(a, b) {
    var aProps = Object.getOwnPropertyNames(a),
        bProps = Object.getOwnPropertynames(b);

    if (aProps.length != bProps.length) {
        return false;
    }

    for (var i = 0; i < aProps.length; i++) {
        var propName = aProps[i];

        if (a[propNames] != b[propNames]) {
            return false;
        }
    }
    return true;
  }
  ```
- What is `true` and `false`?
  Falsy: in JavaScript 6 things are falsy and they are-false, null, undefined, '', 0, NaN

  Truthy: There are only two truthy things - true and everything that is not false.

- As [] is true, [] == true should also be true, right?
  Frist part is right, as for the second part is wrong. `==` will no check **types** when doing equality. 
  For `[] == true`, since both sides are different types, JavaScript can't compare them directly. Hence, JavaScript will try to conver them to the type to compare
