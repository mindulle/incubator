inputmode
=========

The `inputmode` [global attribute](_Resources/Markup%20And%20Styling/html/global_attributes/index.md) is an
[enumerated](https://developer.mozilla.org/en-US/docs/Glossary/Enumerated)
attribute that hints at the type of data that might be entered by the
user while editing the element or its contents. This allows a browser to
display an appropriate virtual keyboard.

It is used primarily on [`<input>`](../element/input) elements, but is
usable on any element in
[`contenteditable`](_Resources/Markup%20And%20Styling/html/global_attributes/index.md#contenteditable) mode.

It\'s important to understand that the `inputmode` attribute doesn\'t
cause any validity requirements to be enforced on input. To require that
input conforms to a particular data type, choose an appropriate
[`<input> element type`](../element/input#input_types). For specific
guidance on choosing [`<input>`](../element/input) types, see the
[Values](#values) section.

Values
------

The attribute can have any of the following values:

[`none`](#none)

:   No virtual keyboard. For when the page implements its own keyboard
    input control.

[`text`](#text) (default value)

:   Standard input keyboard for the user\'s current locale.

[`decimal`](#decimal)

:   Fractional numeric input keyboard containing the digits and decimal
    separator for the user\'s locale (typically [.]).
    Devices may or may not show a minus key ([-]).

[`numeric`](#numeric)

:   Numeric input keyboard, but only requires the digits 0--9. Devices
    may or may not show a minus key.

[`tel`](#tel)

:   A telephone keypad input, including the digits 0--9, the asterisk
    ([\*]) key. Inputs that
    \*require\* a telephone number should typically use
    `<input type="tel">` instead.

[`search`](#search)

:   A virtual keyboard optimized for search input. For instance, the
    [return/submit
    key](https://html.spec.whatwg.org/multipage/interaction.html#input-modalities:-the-enterkeyhint-attribute)
    may be labeled \"Search\", along with possible other optimizations.
    Inputs that *require* a search query should typically use
    `<input type="search">` instead.

[`email`](#email)

:   A virtual keyboard optimized for entering email addresses. Typically
    includes the [@]character as well as other optimizations.
    Inputs that *require* email addresses should typically use
    `<input type="email">` instead.

[`url`](#url)

:   A keypad optimized for entering URLs. This may have the [/]
    key more prominent, for example. Enhanced features could include
    history access and so on. Inputs that *require* a URL should
    typically use `<input type="url">` instead.

Specifications
--------------

  --------------------------------------------------------------------------------------------------

Specification
  --------------------------------------------------------------------------------------------------

  [HTML Standard\
  [\#
  attr-inputmode]](https://html.spec.whatwg.org/multipage/interaction.html#attr-inputmode)

  --------------------------------------------------------------------------------------------------

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

`inputmode`

66

79

9517--23

No

53

No

66

66

79

47

12.2

9.0

See also
--------

- All [global attributes](_Resources/Markup%20And%20Styling/html/global_attributes/index.md).
- [`enterkeyhint`](enterkeyhint) global attribute

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/inputmode>>
