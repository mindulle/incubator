Object.getOwnPropertyDescriptor()
=================================

 
The `Object.getOwnPropertyDescriptor()` static method returns an object
describing the configuration of a specific property on a given object
(that is, one directly present on an object and not in the object\'s
prototype chain). The object returned is mutable but mutating it has no
effect on the original property\'s configuration.


 
Try it 
------

 



 
Syntax
------

 
 
 
[js]


```js
Object.getOwnPropertyDescriptor(obj, prop)
```




 
### Parameters

 

[`obj`](#obj)

:   The object in which to look for the property.

[`prop`](#prop)

:   The name or [`Symbol`](../symbol) of the property whose description
    is to be retrieved.



 
### Return value 

 
A property descriptor of the given property if it exists on the object,
[`undefined`](../undefined) otherwise.



 
Description
-----------

 
This method permits examination of the precise description of a
property. A *property* in JavaScript consists of either a string-valued
name or a [`Symbol`](../symbol) and a property descriptor. Further
information about property descriptor types and their attributes can be
found in [`Object.defineProperty()`](defineproperty).

A *property descriptor* is a record with some of the following
attributes:

[`value`](#value)

:   The value associated with the property (data descriptors only).

[`writable`](#writable)

:   `true` if and only if the value associated with the property may be
    changed (data descriptors only).

[`get`](#get)

:   A function which serves as a getter for the property, or
    [`undefined`](../undefined) if there is no getter (accessor
    descriptors only).

[`set`](#set)

:   A function which serves as a setter for the property, or
    [`undefined`](../undefined) if there is no setter (accessor
    descriptors only).

[`configurable`](#configurable)

:   `true` if and only if the type of this property descriptor may be
    changed and if the property may be deleted from the corresponding
    object.

[`enumerable`](#enumerable)

:   `true` if and only if this property shows up during enumeration of
    the properties on the corresponding object.



 
Examples
--------


 
### Using Object.getOwnPropertyDescriptor() 

 
 
 
[js]


```js
let o, d;

o = {
  get foo() {
    return 17;
  },
};
d = Object.getOwnPropertyDescriptor(o, "foo");
console.log(d);
// {
//   configurable: true,
//   enumerable: true,
//   get: [Function: get foo],
//   set: undefined
// }

o = { bar: 42 };
d = Object.getOwnPropertyDescriptor(o, "bar");
console.log(d);
// {
//   configurable: true,
//   enumerable: true,
//   value: 42,
//   writable: true
// }

o = { [Symbol.for("baz")]: 73 };
d = Object.getOwnPropertyDescriptor(o, Symbol.for("baz"));
console.log(d);
// {
//   configurable: true,
//   enumerable: true,
//   value: 73,
//   writable: true
// }

o = {};
Object.defineProperty(o, "qux", {
  value: 8675309,
  writable: false,
  enumerable: false,
});
d = Object.getOwnPropertyDescriptor(o, "qux");
console.log(d);
// {
//   value: 8675309,
//   writable: false,
//   enumerable: false,
//   configurable: false
// }
```




 
### Non-object coercion 

 
In ES5, if the first argument to this method is not an object (a
primitive), then it will cause a [`TypeError`](../typeerror). In ES2015,
a non-object first argument will be coerced to an object at first.

 
 
[js]


```js
Object.getOwnPropertyDescriptor("foo", 0);
// TypeError: "foo" is not an object  // ES5 code

Object.getOwnPropertyDescriptor("foo", 0);
// Object returned by ES2015 code: {
//   configurable: false,
//   enumerable: true,
//   value: "f",
//   writable: false
// }
```




Specifications
--------------

 
  -----------------------------------------------------------------------------------------------------------------------------------------------
  Specification
  -----------------------------------------------------------------------------------------------------------------------------------------------
  [ECMAScript Language Specification\
  [\#
  sec-object.getownpropertydescriptor]](https://tc39.es/ecma262/multipage/fundamental-objects.html#sec-object.getownpropertydescriptor)

  -----------------------------------------------------------------------------------------------------------------------------------------------


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

`getOwnPropertyDescriptor`

5

12

4

12

5

18

4

12

5

1.0

4.4

1.0

0.10.0

 
See also 
--------

 
-   [`Object.defineProperty()`](defineproperty)
-   [`Reflect.getOwnPropertyDescriptor()`](../reflect/getownpropertydescriptor)



 
© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyDescriptor>

