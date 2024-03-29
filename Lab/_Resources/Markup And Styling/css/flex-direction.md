flex-direction
==============

Baseline: [Widely supported]
---------------------------------------

Baseline is determined by this web feature being supported on the
current and the previous major versions of major browsers.

- [Learn
    more](https://developer.mozilla.org/en-US/blog/baseline-unified-view-stable-web-features/)
- [See full compatibility](#browser_compatibility)

The `flex-direction`
[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) property sets
how flex items are placed in the flex container defining the main axis
and the direction (normal or reversed).

Try it
------

Note that the values `row` and `row-reverse` are affected by the
directionality of the flex container. If its
[`dir`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes#dir)
attribute is `ltr`, `row` represents the horizontal axis oriented from
the left to the right, and `row-reverse` from the right to the left; if
the `dir` attribute is `rtl`, `row` represents the axis oriented from
the right to the left, and `row-reverse` from the left to the right.

Syntax
------

[css]

```css
/* The direction text is laid out in a line */
flex-direction: row;

/* Like <row>, but reversed */
flex-direction: row-reverse;

/* The direction in which lines of text are stacked */
flex-direction: column;

/* Like <column>, but reversed */
flex-direction: column-reverse;

/* Global values */
flex-direction: inherit;
flex-direction: initial;
flex-direction: revert;
flex-direction: revert-layer;
flex-direction: unset;
```

### Values

The following values are accepted:

[`row`](#row)

:   The flex container\'s main-axis is defined to be the same as the
    text direction. The **main-start** and **main-end** points are the
    same as the content direction.

[`row-reverse`](#row-reverse)

:   Behaves the same as `row` but the **main-start** and **main-end**
    points are opposite to the content direction.

[`column`](#column)

:   The flex container\'s main-axis is the same as the block-axis. The
    **main-start** and **main-end** points are the same as the
    **before** and **after** points of the writing-mode.

[`column-reverse`](#column-reverse)

:   Behaves the same as `column` but the **main-start** and **main-end**
    are opposite to the content direction.

Accessibility concerns
----------------------

Using the `flex-direction` property with values of `row-reverse` or
`column-reverse` will create a disconnect between the visual
presentation of content and DOM order. This will adversely affect users
experiencing low vision navigating with the aid of assistive technology
such as a screen reader. If the visual (CSS) order is important, then
screen reader users will not have access to the correct reading order.

- [Flexbox & the keyboard navigation disconnect ---
    Tink](https://tink.uk/flexbox-the-keyboard-navigation-disconnect/)
- [Source Order Matters \| Adrian
    Roselli](https://adrianroselli.com/2015/09/source-order-matters.html)
- [MDN Understanding WCAG, Guideline 1.3
    explanations](https://developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Perceivable#guideline_1.3_%e2%80%94_create_content_that_can_be_presented_in_different_ways)
- [Understanding Success Criterion 1.3.2 \| W3C Understanding WCAG
    2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-sequence.html)

Formal definition
-----------------

  ---------------------------------- -----------------
  [Initial value](initial_value.md)     `row`
  Applies to                         flex containers
  [Inherited](inheritance.md)           no
  [Computed value](computed_value.md)   as specified
  Animation type                     discrete
  ---------------------------------- -----------------

Formal syntax
-------------

```
flex-direction = 
  row             |
  row-reverse     |
  column          |
  column-reverse  
```

Examples
--------

### Reversing flex container columns and rows

#### HTML

[html]

```html
<h4>This is a Column-Reverse</h4>
<div id="col-rev" class="content">
  <div class="box red">A</div>
  <div class="box lightblue">B</div>
  <div class="box yellow">C</div>
</div>
<h4>This is a Row-Reverse</h4>
<div id="row-rev" class="content">
  <div class="box red">A</div>
  <div class="box lightblue">B</div>
  <div class="box yellow">C</div>
</div>
```

#### CSS

[css]

```css
.content {
  width: 200px;
  height: 200px;
  border: 1px solid #c3c3c3;
  display: flex;
}

.box {
  width: 50px;
  height: 50px;
}

#col-rev {
  flex-direction: column-reverse;
}

#row-rev {
  flex-direction: row-reverse;
}

.red {
  background-color: red;
}

.lightblue {
  background-color: lightblue;
}

.yellow {
  background-color: yellow;
}
```

#### Result

Specifications
--------------

  --------------------------------------------------------------------------------------------------

Specification
  --------------------------------------------------------------------------------------------------

  [CSS Flexible Box Layout Module Level 1\
  [\#
  flex-direction-property]](https://drafts.csswg.org/css-flexbox/#flex-direction-property)

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

`flex-direction`

2921

1212

8149

20\[\"Since Firefox 28, multi-line flexbox is supported.\", \"Before
Firefox 81, overflow with `*-reverse` is unsupported. See [bug
1042151](https://bugzil.la/1042151).\"\]

1110

1512.1

97

≤374.4

2925

8149

20\[\"Since Firefox 28, multi-line flexbox is supported.\", \"Before
Firefox 81, overflow with `*-reverse` is unsupported. See [bug
1042151](https://bugzil.la/1042151).\"\]

1412.1

97

2.01.5

See also
--------

- CSS [`flex-flow`](flex-flow.md) shorthand property for the CSS
    `flex-direction` and [`flex-wrap`](flex-wrap.md) properties.
- CSS Flexbox Guide: *[](basic_concepts_of_flexbox.md)*
- CSS Flexbox Guide: *[](ordering_flex_items.md)*

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction>
