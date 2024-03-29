radial-gradient()
=================

The `radial-gradient()`
[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
[function](css_functions.md) creates an image consisting of a
progressive transition between two or more colors that radiate from an
origin. Its shape may be a circle or an ellipse. The function\'s result
is an object of the [`<gradient>`](gradient.md) data type, which is a
special kind of [`<image>`](_Resources/Markup%20And%20Styling/css/image.md).

Try it
------

Syntax
------

[css]

```css
/* A gradient at the center of its container,
   starting red, changing to blue, and finishing green */
radial-gradient(circle at center, red 0, blue, green 100%)
```

A radial gradient is specified by indicating the center of the gradient
(where the 0% ellipse will be) and the size and shape of the *ending
shape* (the 100% ellipse).

### Values

[`<position>`](position_value.md)

:   The position of the gradient, interpreted in the same way as
    [`background-position`](background-position.md) or
    [`transform-origin`](transform-origin.md). If unspecified, it
    defaults to `center`.

[`<ending-shape>`](#ending-shape)

:   The gradient\'s ending-shape. The value can be `circle` (meaning
    that the gradient\'s shape is a circle with a constant radius) or
    `ellipse` (meaning that the shape is an axis-aligned ellipse). If
    unspecified, it defaults to `ellipse`.

[`<size>`](#size)

:   Determines the size of the gradient\'s ending shape. If omitted it
    defaults to farthest-corner. It can be given explicitly or by
    keyword. For the purpose of the keyword definitions, consider the
    gradient box edges as extending infinitely in both directions,
    rather than being finite line segments.

    Both circle and ellipse gradients accept the following keywords for
    their `<size>`:

    
      Keyword             Description
      ------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      `closest-side`      The gradient\'s ending shape meets the side of the box closest to its center (for circles) or meets both the vertical and horizontal sides closest to the center (for ellipses).
      `closest-corner`    The gradient\'s ending shape is sized so that it exactly meets the closest corner of the box from its center.
      `farthest-side`     Similar to `closest-side`, except the ending shape is sized to meet the side of the box farthest from its center (or vertical and horizontal sides).
      `farthest-corner`   The default value, the gradient\'s ending shape is sized so that it exactly meets the farthest corner of the box from its center.
    

    If `<ending-shape>` is specified as `circle`, the size may be given
    explicitly as a [`<length>`](../length), which provides an explicit
    circle radius. Negative values are invalid.

    If `<ending-shape>` is specified as `ellipse`, the size may be given
    as a [`<length-percentage>`](../length-percentage) with two values
    to provide an explicit ellipse size. The first value represents the
    horizontal radius and the second is the vertical radius. Percentage
    values are relative to the corresponding dimension of the gradient
    box. Negative values are invalid.

    When the `<ending-shape>` keyword is omitted, the gradient shape is
    determined by the size given. One `<length>` value provides a
    circle, while two values in `<length-percentage>`units provide an
    ellipse. A single `<percentage>` value is not valid.

[`<linear-color-stop>`](#linear-color-stop)

:   A color-stop\'s [`<color>`](color_value.md) value, followed by one
    or two optional stop positions (either a
    [`<percentage>`](percentage.md) or a [`<length>`](length.md) along
    the gradient\'s axis). A percentage of `0%`, or a length of `0`,
    represents the center of the gradient; the value `100%` represents
    the intersection of the ending shape with the virtual gradient ray.
    Percentage values in between are linearly positioned on the gradient
    ray. Including two stop positions is equivalent to declaring two
    color stops with the same color at the two positions.

[`<color-hint>`](#color-hint)

:   The color-hint is an interpolation hint defining how the gradient
    progresses between adjacent color stops. The length defines at which
    point between two color stops the gradient color should reach the
    midpoint of the color transition. If omitted, the midpoint of the
    color transition is the midpoint between two color stops.

Description
-----------

As with any gradient, a radial gradient has [](_Resources/Markup%20And%20Styling/css/image.md#description); i.e., it has no natural or preferred
size, nor a preferred ratio. Its concrete size will match the size of
the element it applies to.

To create a radial gradient that repeats so as to fill its container,
use the [`repeating-radial-gradient()`](repeating-radial-gradient.md)
function instead.

Because `<gradient>`s belong to the `<image>` data type, they can only
be used where `<image>`s can be used. For this reason,
`radial-gradient()` won\'t work on
[`background-color`](background-color.md) and other properties that use
the [`<color>`](color_value.md) data type.

### Composition of a radial gradient

![Graph explaining radial gradients: the virtual radiant ray is horizontal starting from the midpoint. The elliptical gradient, and therefore the ending shape, has the same aspect ratio as the box upon which it is
declared.](data:image/png;base64,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)

A radial gradient is defined by a *center point*, an *ending shape*, and
two or more *color-stop points*.

To create a smooth gradient, the `radial-gradient()` function draws a
series of concentric shapes radiating out from the center to the *ending
shape* (and potentially beyond). The ending shape may be either a circle
or an ellipse.

Color-stop points are positioned on a *virtual gradient ray* that
extends horizontally from the center towards the right. Percentage-based
color-stop positions are relative to the intersection between the ending
shape and this gradient ray, which represents `100%`. Each shape is a
single color determined by the color on the gradient ray it intersects.

Formal syntax
-------------

```
<radial-gradient()> = 
  radial-gradient( [ <ending-shape> || <size> ]? [ at <position> ]? , <color-stop-list> )  

<position> = 
  [ left | center | right ] || [ top | center | bottom ]  |
  [ left | center | right | <length-percentage> ] [ top | center | bottom | <length-percentage> ]?  |
  [ [ left | right ] <length-percentage> ] && [ [ top | bottom ] <length-percentage> ]  

<color-stop-list> = 
  <linear-color-stop> , [ <linear-color-hint>? , <linear-color-stop> ]#  

<length-percentage> = 
  <length>      |
  <percentage>  

<linear-color-stop> = 
  <color>               &&
  <length-percentage>?  

<linear-color-hint> = 
  <length-percentage>  
```

Examples
--------

### Simple gradient

[css]

```css
.radial-gradient {
  background-image: radial-gradient(cyan 0%, transparent 20%, salmon 40%);
}
```

### Non-centered gradient

[css]

```css
.radial-gradient {
  background-image: radial-gradient(
    farthest-corner at 40px 40px,
    #f35 0%,
    #43e 100%
  );
}
```

### More radial-gradient examples

Please see [Using CSS gradients](using_css_gradients.md) for
more examples.

Specifications
--------------

  -----------------------------------------------------------------------------------

Specification
  -----------------------------------------------------------------------------------

  [CSS Images Module Level 3\
  [\#
  radial-gradients]](https://drafts.csswg.org/css-images/#radial-gradients)

  -----------------------------------------------------------------------------------

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

`radial-gradient`

2613

12

49

16Before Firefox 36, gradients weren\'t applied on the pre-multiplied
color space, leading to shades of grey unexpectedly appearing when used
with transparency.

3.6Since Firefox 42, the prefixed version of gradients can be disabled
by setting `layout.css.prefixes.gradients` to `false`.

10Internet Explorer 5.5 through 9.0 supported gradients via a
proprietary filter:
`-ms-filter: progid:DXImageTransform.Microsoft.Gradient()`.

1512.111.6--15

7

5.1Safari 4 was supporting an experimental `-webkit-gradient(radial,…)`
function. This old outdated syntax is still supported for compatibility
purposes.

≤37≤37

2618

49

16Before Firefox 36, gradients weren\'t applied on the pre-multiplied
color space, leading to shades of grey unexpectedly appearing when used
with transparency.

4Since Firefox 42, the prefixed version of gradients can be disabled by
setting `layout.css.prefixes.gradients` to `false`.

1412.112--14

7

5Safari 4 was supporting an experimental `-webkit-gradient(radial,…)`
function. This old outdated syntax is still supported for compatibility
purposes.

1.51.0

`at`

26

12

49

16Before Firefox 36, gradients weren\'t applied on the pre-multiplied
color space, leading to shades of grey unexpectedly appearing when used
with transparency.

10Since Firefox 42, the prefixed version of gradients can be disabled by
setting `layout.css.prefixes.gradients` to `false`.

10

1511.6--15

7

4.4

26

1610

1412--14

7

1.5

`doubleposition`

71

79

64

No

58

12.1

71

71

64

50

12.2

10.0

`hue_interpolation_method`

111

111

No

No

97

16.2

111

111

No

No

16.2

22.0

`interpolation_color_space`

111

111

No

No

97

16.2

111

111

No

No

16.2

22.0

`interpolation_hints`

40

79

36

No

27

7

40

40

36

27

7

4.0

See also
--------

- [Using CSS gradients](using_css_gradients.md)
- Other gradient functions:
    [`repeating-radial-gradient()`](repeating-radial-gradient.md),
    [`linear-gradient()`](linear-gradient.md),
    [`repeating-linear-gradient()`](repeating-linear-gradient.md),
    [`conic-gradient()`](conic-gradient.md),
    [`repeating-conic-gradient()`](repeating-conic-gradient.md)
- [`<image>`](_Resources/Markup%20And%20Styling/css/image.md)
- [`image()`](_Resources/Markup%20And%20Styling/css/image/image.md)
- [`element()`](element().md)
- [`image-set()`](image-set.md)
- [`cross-fade()`](cross-fade.md)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/gradient/radial-gradient>
