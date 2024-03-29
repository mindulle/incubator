TypeError: can\'t delete non-configurable array element
=======================================================

 
The JavaScript exception \"can\'t delete non-configurable array
element\" occurs when it was attempted to [shorten the
length](../global_objects/array/length#shortening_an_array) of an array,
but one of the array\'s elements is
[non-configurable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#properties).


 
Message
-------

 
```text
TypeError: Cannot delete property '1' of [object Array] (V8-based)
TypeError: can't delete non-configurable array element (Firefox)
TypeError: Unable to delete property. (Safari)
```



 
Error type 
----------

 
[`TypeError`](../global_objects/typeerror)



 
What went wrong? 
----------------

 
It was attempted to [shorten the
length](../global_objects/array/length#shortening_an_array) of an array,
but one of the array\'s elements is
[non-configurable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#properties).
When shortening an array, the elements beyond the new array length will
be deleted, which failed in this situation.

The `configurable` attribute controls whether the property can be
deleted from the object and whether its attributes (other than
`writable`) can be changed.

Usually, properties in an object created by an [array
initializer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#array_literals)
are configurable. However, for example, when using
[`Object.defineProperty()`](../global_objects/object/defineproperty),
the property isn\'t configurable by default.



 
Examples
--------


 
### Non-configurable properties created by Object.defineProperty 

 
The [`Object.defineProperty()`](../global_objects/object/defineproperty)
creates non-configurable properties by default if you haven\'t specified
them as configurable.

 
 
[js]


```js
"use strict";
const arr = [];
Object.defineProperty(arr, 0, { value: 0 });
Object.defineProperty(arr, 1, { value: "1" });

arr.length = 1;
// TypeError: can't delete non-configurable array element
```


You will need to set the elements as configurable, if you intend to
shorten the array.

 
 
[js]


```js
"use strict";
const arr = [];
Object.defineProperty(arr, 0, { value: 0, configurable: true });
Object.defineProperty(arr, 1, { value: "1", configurable: true });

arr.length = 1;
```




 
### Sealed Arrays 

 
The [`Object.seal()`](../global_objects/object/seal) function marks all
existing elements as non-configurable.

 
 
[js]


```js
"use strict";
const arr = [1, 2, 3];
Object.seal(arr);

arr.length = 1;
// TypeError: can't delete non-configurable array element
```


You either need to remove the
[`Object.seal()`](../global_objects/object/seal) call, or make a copy of
it. In case of a copy, shortening the copy of the array does not modify
the original array length.

 
 
[js]


```js
"use strict";
const arr = [1, 2, 3];
Object.seal(arr);

// Copy the initial array to shorten the copy
const copy = Array.from(arr);
copy.length = 1;
// arr.length === 3
```




 
See also 
--------

 
-   [\[\[Configurable\]\]](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#properties)
-   [`length`](../global_objects/array/length)
-   [`Object.defineProperty()`](../global_objects/object/defineproperty)
-   [`Object.seal()`](../global_objects/object/seal)



 
© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Non_configurable_array_element>

