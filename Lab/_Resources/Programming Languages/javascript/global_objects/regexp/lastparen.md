RegExp.lastParen (\$+)
======================

 
 
**Deprecated:** This feature is no longer recommended. Though some
browsers might still support it, it may have already been removed from
the relevant web standards, may be in the process of being dropped, or
may only be kept for compatibility purposes. Avoid using it, and update
existing code if possible; see the [compatibility
table](#browser_compatibility) at the bottom of this page to guide your
decision. Be aware that this feature may cease to work at any time.


 
**Note:** All `RegExp` static properties that expose the last match
state globally are deprecated. See [deprecated RegExp
features](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Deprecated_and_obsolete_features#regexp)
for more information.


The `RegExp.lastParen` static accessor property returns the last
parenthesized substring match, if any. `RegExp["$+"]` is an alias for
this property.


 
Description
-----------

 
Because `lastParen` is a static property of [`RegExp`](../regexp), you
always use it as `RegExp.lastParen` or `RegExp["$+"]`, rather than as a
property of a `RegExp` object you created.

The value of `lastParen` updates whenever a `RegExp` (but not a `RegExp`
subclass) instance makes a successful match. If no matches have been
made, or if the most recent regex execution contains no capturing
groups, `lastParen` is an empty string. The set accessor of `lastParen`
is `undefined`, so you cannot change this property directly.

You cannot use the shorthand alias with the dot property accessor
(`RegExp.$+`), because `+` is not a valid identifier part, so this
causes a [`SyntaxError`](../syntaxerror). Use the [bracket
notation](../../operators/property_accessors) instead.



 
Examples
--------


 
### Using lastParen and \$+ 

 
 
 
[js]


```js
const re = /(hi)/g;
re.test("hi there!");
RegExp.lastParen; // "hi"
RegExp["$+"]; // "hi"
```




Specifications
--------------

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Specification
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [Legacy RegExp features\
  [\#
  additional-properties-of-the-regexp-constructor]](https://github.com/tc39/proposal-regexp-legacy-features/#additional-properties-of-the-regexp-constructor)

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------


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

`lastParen`

1

12

1

10.5

3

18

4

11

1

1.0

4.4

1.0

0.10.0

 
See also 
--------

 
-   [`RegExp.input ($_)`](input)
-   [`RegExp.lastMatch ($&)`](lastmatch)
-   [`` RegExp.leftContext ($`) ``](leftcontext)
-   [`RegExp.rightContext ($')`](rightcontext)
-   [`RegExp.$1, …, RegExp.$9`](n)



 
© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/lastParen>
