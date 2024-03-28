box-shadow
==========

The `box-shadow` [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
property adds shadow effects around an element\'s frame. You can set
multiple effects separated by commas. A box shadow is described by X and
Y offsets relative to the element, blur and spread radius, and color.

Try it
------

The `box-shadow` property enables you to cast a drop shadow from the
frame of almost any element. If a [`border-radius`](border-radius.md) is
specified on the element with a box shadow, the box shadow takes on the
same rounded corners. The z-ordering of multiple box shadows is the same
as multiple [text shadows](text-shadow.md) (the first specified shadow is
on top).

[Box-shadow generator](box-shadow_generator.md)
is an interactive tool allowing you to generate a `box-shadow`.

Syntax
------

[css]

```css
/* Keyword values */
box-shadow: none;

/* A color and two length values */
/* <color> | <length> | <length> */
box-shadow: red 60px -16px;

/* Three length values and a color */
/* <length> | <length> | <length> | <color> */
box-shadow: 10px 5px 5px black;

/* Four length values and a color */
/* <length> | <length> | <length> | <length> | <color> */
box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);

/* inset, length values, and a color */
/* <inset> | <length> | <length> | <color> */
box-shadow: inset 5em 1em gold;

/* Any number of shadows, separated by commas */
box-shadow:
  3px 3px red inset,
  -1em 0 0.4em olive;

/* Global values */
box-shadow: inherit;
box-shadow: initial;
box-shadow: revert;
box-shadow: revert-layer;
box-shadow: unset;
```

Specify a single box-shadow using:

- Two, three, or four [`<length>`](length.md) values.
  - If only two values are given, they are interpreted as
        `<offset-x>` and `<offset-y>` values.
  - If a third value is given, it is interpreted as a
        `<blur-radius>`.
  - If a fourth value is given, it is interpreted as a
        `<spread-radius>`.
- Optionally, the `inset` keyword.
- Optionally, a [`<color>`](#color) value.

To specify multiple shadows, provide a comma-separated list of shadows.

### Values

[`<color>`](#color) [Optional]

:   Specifies color for the shadow. See [`<color>`](color_value.md) values
    for possible keywords and notations. If not specified, the value of
    the [`color`](_Resources/Markup%20And%20Styling/css/color.md) property defined in the parent element is used.

[`<length>`](#length)

:   Specifies the offset length of the shadow. This parameter accepts
    two, three, or four values. Third and fourth values are optional.
    They are interpreted as follows:

    -   If two values are specified, they are interpreted as
        `<offset-x>` (horizontal offset) and `<offset-y>` (vertical
        offset) values. Negative `<offset-x>` value places the shadow to
        the left of the element. Negative `<offset-y>` value places the
        shadow above the element.\
        If not specified, the value of `0` is used for the missing
        length. If both `<offset-x>` and `<offset-y>` are set to `0`,
        the shadow is placed behind the element (and may generate a blur
        effect if `<blur-radius>` and/or `<spread-radius>` is set).

    -   If three values are specified, the third value is interpreted as
        `<blur-radius>`. The larger this value, the bigger the blur, so
        the shadow becomes bigger and lighter. Negative values are not
        allowed. If not specified, it will be set to`0` (meaning that
        the shadow\'s edge will be sharp). The specification does not
        include an exact algorithm for how the blur radius should be
        calculated; however, it does elaborate as follows:

        > ...for a long, straight shadow edge, this should create a
        > color transition the length of the blur distance that is
        > perpendicular to and centered on the shadow\'s edge, and that
        > ranges from the full shadow color at the radius endpoint
        > inside the shadow to fully transparent at the endpoint outside
        > it.

    -   If four values are specified, the fourth value is interpreted as
        `<spread-radius>`. Positive values will cause the shadow to
        expand and grow bigger, negative values will cause the shadow to
        shrink. If not specified, it will be set to `0` (that is, the
        shadow will be the same size as the element).

[`inset`](#inset) [Optional]

:   Changes the shadow from an outer box-shadow to an inner box-shadow
    (as if the content is pressed into the box). Inset shadows are drawn
    inside the box\'s border (even if the border is transparent), and
    they appear above the background but below the content. By default,
    the shadow behaves like a drop shadow, giving the appearance that
    the box is elevated above its content. This is the default behavior
    when `inset` is not specified.

### Interpolation

When animating shadows, such as when multiple shadow values on a box
transition to new values on hover, the values are interpolated.
[Interpolation](https://developer.mozilla.org/en-US/docs/Glossary/Interpolation)
determines intermediate values of properties, such as the blur radius,
spread radius, and color, as shadows transition. For each shadow in a
list of shadows, the color, x, y, blur, and spread transition; the color
as [`<color>`](color_value.md), and the other values as
[`<length>`](length.md)s.

In interpolating multiple shadows between two comma-separated lists of
multiple box shadows, the shadows are paired, in order, with
interpolation occurring between paired shadows. If the lists of shadows
have different lengths, then the shorter list is padded at the end with
shadows whose color is `transparent`, and X, Y, and blur are `0`, with
the inset, or lack of inset, being set to match. If in any pair of
shadows, one has `inset` set and the other does not, the entire shadow
list is uninterpolated; the shadows will change to the new values
without an animating effect.

Formal definition
-----------------

  ---------------------------------- --------------------------------------------------------------------------------
  [Initial value](initial_value.md)     `none`
  Applies to                         all elements. It also applies to [`::first-letter`](::first-letter).
  [Inherited](inheritance.md)           no
  [Computed value](computed_value.md)   any length made absolute; any specified color computed; otherwise as specified
  Animation type                     a [shadow list](box-shadow.md#interpolation)
  ---------------------------------- --------------------------------------------------------------------------------

Formal syntax
-------------

```
box-shadow = 
  none       |
  <shadow>#  

<shadow> = 
  <color>?                                   &&
  [ <length> <length [0,∞]>? <length>? ]  &&
  inset?                                     
```

Examples
--------

### Setting three shadows

In this example, we include three shadows: an inset shadow, a regular
drop shadow, and a 2px shadow that creates a border effect (we could
have used an [`outline`](outline.md) instead for that third shadow).

#### HTML

[html]

```html
<blockquote>
  <q>
    You may shoot me with your words,<br />
    You may cut me with your eyes,<br />
    You may kill me with your hatefulness,<br />
    But still, like air, I'll rise.
  </q>
  <p>&mdash; Maya Angelou</p>
</blockquote>
```

#### CSS

[css]

```css
blockquote {
  padding: 20px;
  box-shadow:
    inset 0 -3em 3em rgba(0, 200, 0, 0.3),
    0 0 0 2px white,
    0.3em 0.3em 1em rgba(200, 0, 0, 0.6);
}
```

#### Result

### Setting zero for offset and blur

When the `x-offset`, `y-offset`, and `blur` are all zero, the box shadow
will be a solid-colored outline of equal-size on all sides. The shadows
are drawn back to front, so the first shadow sits on top of subsequent
shadows. When the `border-radius` is set to 0, as is the default, the
corners of the shadow will be, well, corners. Had we put in a
`border-radius` of any other value, the corners would have been rounded.

We added a margin the size of the widest box-shadow to ensure the shadow
doesn\'t overlap adjacent elements or go beyond the border of the
containing box. A box-shadow does not impact [box model](css_box_model.md)
dimensions.

#### HTML

[html]

```html
<div><p>Hello World</p></div>
```

#### CSS

[css]

```css
p {
  box-shadow:
    0 0 0 2em #f4aab9,
    0 0 0 4em #66ccff;
  margin: 4em;
  padding: 1em;
}
```

#### Result

Specifications
--------------

  ----------------------------------------------------------------------------

Specification
  ----------------------------------------------------------------------------

  [CSS Backgrounds and Borders Module Level 3\
  [\#
  box-shadow]](https://drafts.csswg.org/css-backgrounds/#box-shadow)

  ----------------------------------------------------------------------------

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

`box-shadow`

10Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

1

12

49

4Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

3.5--13

9\[\"To use `box-shadow` in Internet Explorer 9 or later, you must set
[`border-collapse`](https://developer.mozilla.org/docs/Web/CSS/border-collapse)
to `separate`.\", \"Since version 5.5, Internet Explorer supports
Microsoft\'s
[DropShadow](https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms532985(v=vs.85))
and [Shadow
Filter](https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms533086(v=vs.85)).
You can use this proprietary extension to cast a drop shadow (though the
syntax and the effect are different from CSS3)\"\]

10.5Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

5.1Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

3

≤37Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

≤37

18Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

18

49

4Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

4--14

14Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

14

5Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

1

1.0Shadows affect layout in this browser. For example, if you cast an
outer shadow to a box with a `width` of `100%`, then you\'ll see a
scrollbar.

1.0

`inset`

101

12

43.5--13

9\[\"To use `box-shadow` in Internet Explorer 9 or later, you must set
[`border-collapse`](https://developer.mozilla.org/docs/Web/CSS/border-collapse)
to `separate`.\", \"`inset` must be the last keyword in the
declaration.\"\]

10.5

5.15

≤37≤37

1818

44--14

1414

54.2

1.01.0

`multiple_shadows`

101

12

43.5--13

9To use `box-shadow` in Internet Explorer 9 or later, you must set
[`border-collapse`](https://developer.mozilla.org/docs/Web/CSS/border-collapse)
to `separate`.

10.5

5.13

≤37≤37

1818

44--14

1414

51

1.01.0

`spread_radius`

101

12

43.5--13

9To use `box-shadow` in Internet Explorer 9 or later, you must set
[`border-collapse`](https://developer.mozilla.org/docs/Web/CSS/border-collapse)
to `separate`.

10.5

5.15

≤37≤37

1818

44--14

1414

54.2

1.01.0

See also
--------

- The [`<color>`](color_value.md) data type (for specifying the shadow
    color)
- [`text-shadow`](text-shadow.md)
- [`drop-shadow()`](drop-shadow.md)
- [](applying_color.md)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow>