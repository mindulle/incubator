SyntaxError: missing } after property list
==========================================

 
The JavaScript exception \"missing } after property list\" occurs when
there is a mistake in the [object
initializer](../operators/object_initializer) syntax somewhere. Might be
in fact a missing curly bracket, but could also be a missing comma.


 
Message
-------

 
```text
SyntaxError: missing } after property list (Firefox)
SyntaxError: Unexpected identifier 'c'. Expected '}' to end an object literal. (Safari)
```



 
Error type 
----------

 
[`SyntaxError`](../global_objects/syntaxerror)



 
What went wrong? 
----------------

 
There is a mistake in the [object
initializer](../operators/object_initializer) syntax somewhere. Might be
in fact a missing curly bracket, but could also be a missing comma, for
example. Also check if any closing curly braces or parenthesis are in
the correct order. Indenting or formatting the code a bit nicer might
also help you to see through the jungle.



 
Examples
--------


 
### Forgotten comma 

 
Oftentimes, there is a missing comma in your object initializer code:

 
 
[js]


```js
const obj = {
  a: 1,
  b: { myProp: 2 }
  c: 3
};
```


Correct would be:

 
 
[js]


```js
const obj = {
  a: 1,
  b: { myProp: 2 },
  c: 3,
};
```




 
See also 
--------

 
-   [Object initializer](../operators/object_initializer)



 
© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_curly_after_property_list>

