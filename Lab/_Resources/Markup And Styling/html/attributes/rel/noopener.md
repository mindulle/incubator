rel=noopener
============

The `noopener` keyword for the [`rel`](../rel) attribute of the
[`<a>`](../../element/a), [`<area>`](../../element/area), and
[`<form>`](../../element/form) elements instructs the browser to
navigate to the target resource without granting the new browsing
context access to the document that opened it --- by not setting the
[`Window.opener`](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener)
property on the opened window (it returns `null`).

This is especially useful when opening untrusted links, in order to
ensure they cannot tamper with the originating document via the
[`Window.opener`](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener)
property (see [About
rel=noopener](https://mathiasbynens.github.io/rel-noopener/) for more
details), while still providing the `Referer` HTTP header (unless
`noreferrer` is used as well).

Note that when `noopener` is used, nonempty target names other than
`_top`, `_self`, and `_parent` are all treated like `_blank` in terms of
deciding whether to open a new window/tab.

**Note:** Setting `target="_blank"` on `<a>` elements now implicitly
provides the same `rel` behavior as setting `rel="noopener"` which does
not set `window.opener`. See [browser
compatibility](../../element/a#browser_compatibility) for support
status.

Specifications
--------------

  ----------------------------------------------------------------------------------------------------

Specification
  ----------------------------------------------------------------------------------------------------

  [HTML Standard\
  [\#
  link-type-noopener]](https://html.spec.whatwg.org/multipage/links.html#link-type-noopener)

  ----------------------------------------------------------------------------------------------------

Browser compatibility
---------------------

Desktop

Mobile

Chrome

Edge

Firefox

Internet Explorer

Opera

Safari

WebView Android

Chrome Android

Firefox for Android

Opera Android

Safari on IOS

Samsung Internet

`noopener`

49

79

52Before Firefox 63, `rel="noopener"` created windows with all features
disabled by default. Starting with Firefox 63, these windows have the
same features enabled by default as any other window.

No

36

10.1

49

49

52Before Firefox 63, `rel="noopener"` created windows with all features
disabled by default. Starting with Firefox 63, these windows have the
same features enabled by default as any other window.

36

10.3

5.0

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/rel/noopener>>
