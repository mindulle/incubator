Less than or equal (\<=)
========================

 
The `<=` operator returns `true` if the left operand is less than or
equal to the right operand, and `false` otherwise.


 
Try it 
------

 



 
Syntax
------

 
 
 
[js]


```js
x <= y
```




 
Description
-----------

 
The operands are compared using the same algorithm as the [Less
than](less_than) operator, with the operands swapped and the result
negated. `x <= y` is generally equivalent to `!(y < x)`, except for two
cases where `x <= y` and `x > y` are both `false`:

-   If one of the operands gets converted to a BigInt, while the other
    gets converted to a string that cannot be converted to a BigInt
    value (it throws a [syntax error](../errors/invalid_bigint_syntax)
    when passed to [`BigInt()`](../global_objects/bigint/bigint)).
-   If one of the operands gets converted to `NaN`. (For example,
    strings that cannot be converted to numbers, or `undefined`.)

In addition, `x <= y` coerces `x` to a primitive before `y`, while
`y < x` coerces `y` to a primitive before `x`. Because coercion may have
side effects, the order of the operands may matter.

`x <= y` is generally equivalent to `x < y || x == y`, except for a few
cases:

-   When one of `x` or `y` is `null`, and the other is something that\'s
    not `null` and becomes 0 when [coerced to
    numeric](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#numeric_coercion)
    (including `0`, `0n`, `false`, `""`, `"0"`, `new Date(0)`, etc.):
    `x <= y` is `true`, while `x < y || x == y` is `false`.
-   When one of `x` or `y` is `undefined`, and the other is one of
    `null` or `undefined`: `x <= y` is `false`, while `x == y` is
    `true`.
-   When `x` and `y` are the same object that becomes `NaN` after the
    first step of [Less than](less_than) (such as `new Date(NaN)`):
    `x <= y` is `false`, while `x == y` is `true`.
-   When `x` and `y` are different objects that become the same value
    after the first step of [Less than](less_than): `x <= y` is `true`,
    while `x < y || x == y` is `false`.



 
Examples
--------


 
### String to string comparison 

 
 
 
[js]


```js
"a" <= "b"; // true
"a" <= "a"; // true
"a" <= "3"; // false
```




 
### String to number comparison 

 
 
 
[js]


```js
"5" <= 3; // false
"3" <= 3; // true
"3" <= 5; // true

"hello" <= 5; // false
5 <= "hello"; // false
```




 
### Number to Number comparison 

 
 
 
[js]


```js
5 <= 3; // false
3 <= 3; // true
3 <= 5; // true
```




 
### Number to BigInt comparison 

 
 
 
[js]


```js
5n <= 3; // false
3 <= 3n; // true
3 <= 5n; // true
```




 
### Comparing Boolean, null, undefined, NaN 

 
 
 
[js]


```js
true <= false; // false
true <= true; // true
false <= true; // true

true <= 0; // false
true <= 1; // true

null <= 0; // true
1 <= null; // false

undefined <= 3; // false
3 <= undefined; // false

3 <= NaN; // false
NaN <= 3; // false
```




Specifications
--------------

 
  -------------------------------------------------------------------------------------------------------------------------------------
  Specification
  -------------------------------------------------------------------------------------------------------------------------------------
  [ECMAScript Language Specification\
  [\#
  sec-relational-operators]](https://tc39.es/ecma262/multipage/ecmascript-language-expressions.html#sec-relational-operators)

  -------------------------------------------------------------------------------------------------------------------------------------


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

`Less_than_or_equal`

1

12

1

3

1

18

4

10.1

1

1.0

4.4

1.0

0.10.0

 
See also 
--------

 
-   [Greater than (`>`)](greater_than)
-   [Greater than or equal (`>=`)](greater_than_or_equal)
-   [Less than (`<`)](less_than)



 
© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Less_than_or_equal>

