＃Algorithm in JavaScript.md

### Remove Dupicate
Q: How would you remove duplicate members from an array?
Hint: use an object.
```
function removeDuplicate(arr) {
    var exists = {},
        outArr = [],
        elm;

    for (var i = 0, len = arr.length; i < len; i++) {
        elm = arr[i];
        if (!exists[elm]) {
            outArr.push(elm);
            exists[elm] = true;
        }
    }
    return outArr;
}
```

### Merge Two Sorted Array

Question: How would you merge two sorted array?

```
function mergSortedArray(a, b) {
    var merged = [],
        aElm = a[0],
        bElm = b[0],
        i = 1,
        j = 1;

    if (a.length == 0) {
        return b;
    }
    if (b.length == 0) {
        return a;
    }

    while (aElm || bElm) {
        if ((aElm && !bElm) || aElm < bElm) {
            merged.push(aElm);
            aElm = a[i++];
        } else {
            merged.push[bElm];
            bElm = b[j++];
        }
    }

    return merged;
}
```

### Swap Number without Temp
Question: How would you swap two numbers without using a temporary variable?


```
function swapNumb (a, b) {
    b = b - a;
    a = a + b;
    b = a - b;
}
```


### Reverse String

```
function reverse(str) {
    var rtnStr ='';
    for(var i = str.length - 1; i >= 0; i--) {
        rtnStr +=str[i];
    }
    return rtnStr;
}

----------

O(n) solution: 

function reverse(str) {
    var rtnStr = [];
    if (!str || typeof str != 'string' || str.length < 2) {
        return str;
    }

    for (var i = str.length - 1; i >= 0; i--) {
        rtnStr.push(str[i]);
    }
    return rtnStr.join('');
}

----------


```




