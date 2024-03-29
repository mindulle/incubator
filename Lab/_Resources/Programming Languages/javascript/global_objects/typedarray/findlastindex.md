TypedArray.prototype.findLastIndex()
====================================

 
The `findLastIndex()` method of [`TypedArray`](../typedarray) instances
iterates the typed array in reverse order and returns the index of the
first element that satisfies the provided testing function. If no
elements satisfy the testing function, -1 is returned. This method has
the same algorithm as
[`Array.prototype.findLastIndex()`](../array/findlastindex).


 
Try it 
------

 



 
Syntax
------

 
 
 
[js]


```js
findLastIndex(callbackFn)
findLastIndex(callbackFn, thisArg)
```




 
### Parameters

 

[`callbackFn`](#callbackfn)

:   A function to execute for each element in the typed array. It should
    return a
    [truthy](https://developer.mozilla.org/en-US/docs/Glossary/Truthy)
    value to indicate a matching element has been found, and a
    [falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)
    value otherwise. The function is called with the following
    arguments:

    [`element`](#element)

    :   The current element being processed in the typed array.

    [`index`](#index)

    :   The index of the current element being processed in the typed
        array.

    [`array`](#array)

    :   The typed array `findLastIndex()` was called upon.

[`thisArg`](#thisarg) [Optional]

:   A value to use as `this` when executing `callbackFn`. See [iterative
    methods](../array#iterative_methods).



 
### Return value 

 
The index of the last (highest-index) element in the typed array that
passes the test. Otherwise `-1` if no matching element is found.



 
Description
-----------

 
See [`Array.prototype.findLastIndex()`](../array/findlastindex) for more
details. This method is not generic and can only be called on typed
array instances.



 
Examples
--------


 
### Find the index of the last prime number in a typed array 

 
The following example returns the index of the last element in the typed
array that is a prime number, or `-1` if there is no prime number.

 
 
[js]


```js
function isPrime(element) {
  if (element % 2 === 0 || element < 2) {
    return false;
  }
  for (let factor = 3; factor <= Math.sqrt(element); factor += 2) {
    if (element % factor === 0) {
      return false;
    }
  }
  return true;
}

let uint8 = new Uint8Array([4, 6, 8, 12]);
console.log(uint8.findLastIndex(isPrime));
// -1 (no primes in array)
uint8 = new Uint8Array([4, 5, 7, 8, 9, 11, 12]);
console.log(uint8.findLastIndex(isPrime));
// 5
```




Specifications
--------------

 
  -----------------------------------------------------------------------
  Specification
  -----------------------------------------------------------------------
  [ECMAScript Language Specification\
  [\# sec-%typedarray%.prototype.findlastindex]](#)

  -----------------------------------------------------------------------


Browser compatibility 
---------------------

 


Desktop

Mobile

Server

Chrome

Edge

Firefox

Opera

Safari

Chrome Android

Firefox for Android

Opera Android

Safari on IOS

Samsung Internet

WebView Android

Deno

Node.js

`findLastIndex`

97

97

104

83

15.4

97

104

68

15.4

18.0

97

1.16

No

 
See also 
--------

 
-   [Polyfill of `TypedArray.prototype.findLastIndex` in
    `core-js`](https://github.com/zloirock/core-js#array-find-from-last)
-   [JavaScript typed
    arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Typed_arrays)
    guide
-   [`TypedArray`](../typedarray)
-   [`TypedArray.prototype.find()`](find)
-   [`TypedArray.prototype.findIndex()`](findindex)
-   [`TypedArray.prototype.findLast()`](findlast)
-   [`TypedArray.prototype.indexOf()`](indexof)
-   [`TypedArray.prototype.lastIndexOf()`](lastindexof)
-   [`Array.prototype.findLastIndex()`](../array/findlastindex)



 
© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray/findLastIndex>

