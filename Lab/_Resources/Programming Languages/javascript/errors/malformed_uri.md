URIError: malformed URI sequence
================================

 
The JavaScript exception \"malformed URI sequence\" occurs when URI
encoding or decoding wasn\'t successful.


 
Message
-------

 
```text
URIError: URI malformed (V8-based)
URIError: malformed URI sequence (Firefox)
URIError: String contained an illegal UTF-16 sequence. (Safari)
```



 
Error type 
----------

 
[`URIError`](../global_objects/urierror)



 
What went wrong? 
----------------

 
URI encoding or decoding wasn\'t successful. An argument given to either
the [`decodeURI`](../global_objects/decodeuri),
[`encodeURI`](../global_objects/encodeuri),
[`encodeURIComponent`](../global_objects/encodeuricomponent), or
[`decodeURIComponent`](../global_objects/decodeuricomponent) function
was not valid, so that the function was unable encode or decode
properly.



 
Examples
--------


 
### Encoding

 
Encoding replaces each instance of certain characters by one, two,
three, or four escape sequences representing the UTF-8 encoding of the
character. An [`URIError`](../global_objects/urierror) will be thrown if
there is an attempt to encode a surrogate which is not part of a
high-low pair, for example:

 
 
[js]


```js
encodeURI("\uD800");
// "URIError: malformed URI sequence"

encodeURI("\uDFFF");
// "URIError: malformed URI sequence"
```


A high-low pair is OK. For example:

 
 
[js]


```js
encodeURI("\uD800\uDFFF");
// "%F0%90%8F%BF"
```




 
### Decoding

 
Decoding replaces each escape sequence in the encoded URI component with
the character that it represents. If there isn\'t such a character, an
error will be thrown:

 
 
[js]


```js
decodeURIComponent("%E0%A4%A");
// "URIError: malformed URI sequence"
```


With proper input, this should usually look like something like this:

 
 
[js]


```js
decodeURIComponent("JavaScript_%D1%88%D0%B5%D0%BB%D0%BB%D1%8B");
// "JavaScript_шеллы"
```




 
See also 
--------

 
-   [`URIError`](../global_objects/urierror)
-   [`decodeURI`](../global_objects/decodeuri)
-   [`encodeURI`](../global_objects/encodeuri)
-   [`encodeURIComponent`](../global_objects/encodeuricomponent)
-   [`decodeURIComponent`](../global_objects/decodeuricomponent)



 
© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Malformed_URI>

