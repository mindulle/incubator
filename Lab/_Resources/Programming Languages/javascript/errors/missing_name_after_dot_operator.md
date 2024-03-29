SyntaxError: missing name after . operator
==========================================

 
The JavaScript exception \"missing name after . operator\" occurs when
there is a problem with how the dot operator (`.`) is used for [property
access](../operators/property_accessors).


 
Message
-------

 
```text
SyntaxError: missing name after . operator (Firefox)
SyntaxError: Unexpected token '['. Expected a property name after '.'. (Safari)
```



 
Error type 
----------

 
[`SyntaxError`](../global_objects/syntaxerror)



 
What went wrong? 
----------------

 
The dot operator (`.`) is used for [property
access](../operators/property_accessors). You will have to specify the
name of the property that you want to access. For computed property
access, you might need to change your property access from using a dot
to using square brackets. These will allow you to compute an expression.
Maybe you intended to do concatenation instead? A plus operator (`+`) is
needed in that case. Please see the examples below.



 
Examples
--------


 
### Property access 

 
[Property accessors](../operators/property_accessors) in JavaScript use
either the dot (.) or square brackets (`[]`), but not both. Square
brackets allow computed property access.

 
 
[js]


```js
const obj = { foo: { bar: "baz", bar2: "baz2" } };
const i = 2;

obj.[foo].[bar]
// SyntaxError: missing name after . operator

obj.foo."bar"+i;
// SyntaxError: missing name after . operator
```


To fix this code, you need to access the object like this:

 
 
[js]


```js
obj.foo.bar; // "baz"
// or alternatively
obj["foo"]["bar"]; // "baz"

// computed properties require square brackets
obj.foo["bar" + i]; // "baz2"
// or as template literal
obj.foo[`bar${i}`]; // "baz2"
```




 
### Property access vs. concatenation 

 
If you are coming from another programming language (like
[PHP](https://developer.mozilla.org/en-US/docs/Glossary/PHP)), it is
also easy to mix up the dot operator (`.`) and the concatenation
operator (`+`).

 
 
[js]


```js
console.log("Hello" . "world");

// SyntaxError: missing name after . operator
```


Instead you need to use a plus sign for concatenation:

 
 
[js]


```js
console.log("Hello" + "World");
```




 
See also 
--------

 
-   [Property accessors](../operators/property_accessors)



 
© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_name_after_dot_operator>

