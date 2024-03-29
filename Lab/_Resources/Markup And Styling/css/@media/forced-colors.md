forced-colors
=============

The `forced-colors`
[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) [](@media.md#media_features) is used to detect if the [user
agent](https://developer.mozilla.org/en-US/docs/Glossary/User_agent) has
enabled a forced colors mode where it enforces a user-chosen limited
color palette on the page. An example of a forced colors mode is Windows
High Contrast mode.

Syntax
------

The `forced-colors` media feature indicates whether or not the browser
is currently in forced-colors mode.

### Values

[`none`](#none)

:   Forced colors mode is not active; the page\'s colors are not being
    forced into a limited palette.

[`active`](#active)

:   Indicates that forced colors mode is active. The browser provides
    the color palette to authors through the [](system-color.md) keywords and, if appropriate, triggers the
    appropriate value of [`prefers-color-scheme`](prefers-color-scheme.md)
    so that authors can adapt the page. The browser selects the value
    for `prefers-color-scheme` based on the lightness of the `Canvas`
    system color (see the [color adjust
    spec](https://www.w3.org/TR/css-color-adjust-1/#forced) for more
    details).

Usage notes
-----------

### Properties affected by forced-color mode

In forced colors mode, the values of the following properties are
treated as if they have no author-level values specified. That is,
browser-specified values are used instead. The browser-specified values
do not affect the style cascade; the values are instead forced by the
browser at paint time.

These browser-specified values are selected from the set of system
colors --- this ensures a consistent contrast for common UI elements for
users that have forced colors enabled.

- [`color`](_Resources/Markup%20And%20Styling/css/color.md)
- [`background-color`](background-color.md)
- [`text-decoration-color`](text-decoration-color.md)
- [`text-emphasis-color`](text-emphasis-color.md)
- [`border-color`](border-color.md)
- [`outline-color`](outline-color.md)
- [`column-rule-color`](column-rule-color.md)
- [`-webkit-tap-highlight-color`](-webkit-tap-highlight-color.md)
- [SVG fill
    attribute](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/fill)
- [SVG stroke
    attribute](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/stroke)

Additionally the following properties have special behavior in forced
colors mode:

- [`box-shadow`](box-shadow.md) is forced to \'none\'
- [`text-shadow`](text-shadow.md) is forced to \'none\'
- [`background-image`](background-image.md) is forced to \'none\' for
    values that are not url-based
- [`color-scheme`](color-scheme.md) is forced to \'light dark\'
- [`scrollbar-color`](scrollbar-color.md) is forced to \'auto\'

The system colors that are forced for the above properties depend on the
context of the element. For example the [`color`](_Resources/Markup%20And%20Styling/css/color.md) property on
button element will be forced to `ButtonText`. On normal text it will be
forced to `CanvasText`. See the [](color_value.md#system_colors) for additional details of when
each might be appropriate in various UI contexts.

**Note:** user agents choose system colors based on native element
semantics, *not* on added ARIA roles. As an example, adding
`role="button"` to a `div` will **not** cause an element\'s color to be
forced to `ButtonText`

In addition to these adjustments, browsers will help ensure text
legibility by drawing \"backplates\" behind text. This is particularly
important for preserving contrast when text is placed on top of images.

There are two cases where the user agent does not force the values for
the above properties --- when a
[`forced-color-adjust`](forced-color-adjust.md) value of `none` is
applied to an element, or when a system color is specified by the
author.

When forced-color-adjust is set to `none` on an element, none of the
forced color values will apply, and author styles will be applied as
normal. Additionally, the backplate for text will be disabled.

When a system color is specified, it will be used instead of the value
that would otherwise have been forced.

You can also use system colors with any property *other* than those
listed above, to ensure that the rest of the page integrates with the
restricted color palette available in forced colors mode.

### Accessibility concerns

In general, web authors should **not** be using the `forced-colors`
media feature to create a separate design for users with this feature
enabled. Instead, its intended usage is to make small tweaks to improve
usability or legibility when the default application of forced colors
does not work well for a given portion of a page.

The high contrast provided by forced colors mode\'s reduced palette and
text backplates is often essential for some users to be able to read or
use a given website, so adjustments that affect content should be chosen
carefully and targeted to content that is otherwise not legible.

### User preferences

This media feature is active only if the user has enabled color scheme
preferences in their operating system. One example of such a feature is
High Contrast mode on Windows.

Examples
--------

**Note:** The below example will only work when using a browser that
supports this media feature, and with a preference such as High Contrast
mode enabled in your OS.

This example is a button that normally gets its contrast via
[`box-shadow`](box-shadow.md). Under forced colors mode, box-shadow is
forced to none, so the example uses the forced-colors media feature to
ensure there is a border of the appropriate color (ButtonText in this
case)

### HTML

[html]

```html
<button class="button">Press me!</button>
```

### CSS

[css]

```css
.button {
  border: 0;
  padding: 10px;
  box-shadow:
    -2px -2px 5px gray,
    2px 2px 5px gray;
}

@media (forced-colors: active) {
  .button {
    /* Use a border instead, since box-shadow is forced to 'none' in forced-colors mode */
    border: 2px ButtonText solid;
  }
}
```

### Result

Specifications
--------------

  ---------------------------------------------------------------------------------

Specification
  ---------------------------------------------------------------------------------

  [Media Queries Level 5\
  [\#
  forced-colors]](https://drafts.csswg.org/mediaqueries-5/#forced-colors)

  ---------------------------------------------------------------------------------

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

`forced-colors`

89

79

89

No

75

16

89

89

89

63

16

15.0

See also
--------

- [\@media](@media.md)
- [Styling for Windows high contrast with standards for forced
    colors.](https://blogs.windows.com/msedgedev/2020/09/17/styling-for-windows-high-contrast-with-new-standards-for-forced-colors/)
- [`forced-color-adjust`](forced-color-adjust.md)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/@media/forced-colors>
