:nth-child()
============

The `:nth-child()`
[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
[pseudo-class](pseudo-classes.md) matches elements based on the indexes of
the elements in the child list of their parents. In other words, the
`:nth-child()` selector selects child elements according to their
position among all the sibling elements within a parent element.

Try it
------

**Note:** In the `element:nth-child()` syntax, the child count includes
sibling children of any element type; but it is considered a match only
if the element *at that child position* matches the other components of
the selector.

Syntax
------

`:nth-child()` takes a single argument that describes a pattern for
matching element indices in a list of siblings. Element indices are
1-based.

[css]

```css
:nth-child(<nth> [of <complex-selector-list>]?) {
  /* ... */
}
```

### Keyword values

[`odd`](#odd)

:   Represents elements whose numeric position in a series of siblings
    is odd: 1, 3, 5, etc.

[`even`](#even)

:   Represents elements whose numeric position in a series of siblings
    is even: 2, 4, 6, etc.

### Functional notation

[`<An+B>`](#anb)

:   Represents elements whose numeric position in a series of siblings
    matches the pattern `An+B`, for every positive integer or zero value
    of `n`, where:

    -   `A` is an integer step size,
    -   `B` is an integer offset,
    -   `n` is all nonnegative integers, starting from 0.

    It can be read as the `An+B`-th element of a list. The `A` and `B`
    must both have [`<integer>`](integer) values.

### The `of <selector>` syntax

By passing a selector argument, we can select the **nth** element that
matches that selector. For example, the following selector matches the
first three list items which have a `class="important"` set.

[css]

```css
:nth-child(-n + 3 of li.important) {
}
```

This is different from moving the selector outside of the function,
like:

[css]

```css
li.important:nth-child(-n + 3) {
}
```

This selector selects list items if they are among the first three
children and match the selector `li.important`.

Examples
--------

### Example selectors

[`tr:nth-child(odd)`](#trnth-childodd) or `tr:nth-child(2n+1)`

:   Represents the odd rows of an HTML table: 1, 3, 5, etc.

[`tr:nth-child(even)`](#trnth-childeven) or `tr:nth-child(2n)`

:   Represents the even rows of an HTML table: 2, 4, 6, etc.

[`:nth-child(7)`](#nth-child7)

:   Represents the seventh element.

[`:nth-child(5n)`](#nth-child5n)

:   Represents elements **5** \[=5×1\], **10** \[=5×2\], **15**
    \[=5×3\], **etc.** The first one to be returned as a result of the
    formula is **0** \[=5x0\], resulting in a no-match, since the
    elements are indexed from 1, whereas `n` starts from 0. This may
    seem weird at first, but it makes more sense when the `B` part of
    the formula is `>0`, like in the next example.

[`:nth-child(n+7)`](#nth-childn7)

:   Represents the seventh and all following elements: **7** \[=0+7\],
    **8** \[=1+7\], **9** \[=2+7\], **etc.**

[`:nth-child(3n+4)`](#nth-child3n4)

:   Represents elements **4** \[=(3×0)+4\], **7** \[=(3×1)+4\], **10**
    \[=(3×2)+4\], **13** \[=(3×3)+4\], **etc.**

[`:nth-child(-n+3)`](#nth-child-n3)

:   Represents the first three elements. \[=-0+3, -1+3, -2+3\]

[`p:nth-child(n)`](#pnth-childn)

:   Represents every `<p>` element in a group of siblings. This selects
    the same elements as a simple `p` selector (although with a higher
    specificity).

[`p:nth-child(1)`](#pnth-child1) or `p:nth-child(0n+1)`

:   Represents every `<p>` that is the first element in a group of
    siblings. This is the same as the [`:first-child`](:first-child)
    selector (and has the same specificity).

[`p:nth-child(n+8):nth-child(-n+15)`](#pnth-childn8nth-child-n15)

:   Represents the eighth through the fifteenth `<p>` elements of a
    group of siblings.

### Detailed example

#### HTML

[html]

```html
<h3>
  <code>span:nth-child(2n+1)</code>, WITHOUT an <code>&lt;em&gt;</code> among
  the child elements.
</h3>
<p>Children 1, 3, 5, and 7 are selected.</p>
<div class="first">
  <span>Span 1!</span>
  <span>Span 2</span>
  <span>Span 3!</span>
  <span>Span 4</span>
  <span>Span 5!</span>
  <span>Span 6</span>
  <span>Span 7!</span>
</div>

<br />

<h3>
  <code>span:nth-child(2n+1)</code>, WITH an <code>&lt;em&gt;</code> among the
  child elements.
</h3>
<p>
  Children 1, 5, and 7 are selected.<br />
  3 is used in the counting because it is a child, but it isn't selected because
  it isn't a <code>&lt;span&gt;</code>.
</p>
<div class="second">
  <span>Span!</span>
  <span>Span</span>
  <em>This is an `em`.</em>
  <span>Span</span>
  <span>Span!</span>
  <span>Span</span>
  <span>Span!</span>
  <span>Span</span>
</div>

<br />

<h3>
  <code>span:nth-of-type(2n+1)</code>, WITH an <code>&lt;em&gt;</code> among the
  child elements.
</h3>
<p>
  Children 1, 4, 6, and 8 are selected.<br />
  3 isn't used in the counting or selected because it is an
  <code>&lt;em&gt;</code>, not a <code>&lt;span&gt;</code>, and
  <code>nth-of-type</code> only selects children of that type. The
  <code>&lt;em&gt;</code> is completely skipped over and ignored.
</p>
<div class="third">
  <span>Span!</span>
  <span>Span</span>
  <em>This is an `em`.</em>
  <span>Span!</span>
  <span>Span</span>
  <span>Span!</span>
  <span>Span</span>
  <span>Span!</span>
</div>
```

#### CSS

[css]

```css
.first span:nth-child(2n + 1),
.second span:nth-child(2n + 1),
.third span:nth-of-type(2n + 1) {
  background-color: tomato;
}
```

#### Result

### Using \'of \<selector\>\'

In this example there is an unordered list of names, some of them have
been marked as **noted** using `class="noted"`. These have been
highlighted with a thick bottom border.

#### HTML

[html]

```html
<ul>
  <li class="noted">Diego</li>
  <li>Shilpa</li>
  <li class="noted">Caterina</li>
  <li>Jayla</li>
  <li>Tyrone</li>
  <li>Ricardo</li>
  <li class="noted">Gila</li>
  <li>Sienna</li>
  <li>Titilayo</li>
  <li class="noted">Lexi</li>
  <li>Aylin</li>
  <li>Leo</li>
  <li>Leyla</li>
  <li class="noted">Bruce</li>
  <li>Aisha</li>
  <li>Veronica</li>
  <li class="noted">Kyouko</li>
  <li>Shireen</li>
  <li>Tanya</li>
  <li class="noted">Marlene</li>
</ul>
```

#### CSS

In the following CSS we are targeting the **even** list items that are
marked with `class="noted"`.

[css]

```css
li:nth-child(even of .noted) {
  background-color: tomato;
  border-bottom-color: seagreen;
}
```

#### Result

Items with `class="noted"` have a thick bottom border and items 3, 10
and 17 have a solid background as they are the *even* list items with
`class="noted"`.

### of selector syntax vs selector nth-child

In this example, there are two unordered lists of names. The first list
shows the effect of `li:nth-child(-n + 3 of .noted)` and the second list
shows the effect of `li.noted:nth-child(-n + 3)`.

#### HTML

[html]

```html
<ul class="one">
  <li class="noted">Diego</li>
  <li>Shilpa</li>
  <li class="noted">Caterina</li>
  <li>Jayla</li>
  <li>Tyrone</li>
  <li>Ricardo</li>
  <li class="noted">Gila</li>
  <li>Sienna</li>
  <li>Titilayo</li>
  <li class="noted">Lexi</li>
</ul>
<ul class="two">
  <li class="noted">Diego</li>
  <li>Shilpa</li>
  <li class="noted">Caterina</li>
  <li>Jayla</li>
  <li>Tyrone</li>
  <li>Ricardo</li>
  <li class="noted">Gila</li>
  <li>Sienna</li>
  <li>Titilayo</li>
  <li class="noted">Lexi</li>
</ul>
```

#### CSS

[css]

```css
ul.one > li:nth-child(-n + 3 of .noted) {
  background-color: tomato;
  border-bottom-color: seagreen;
}

ul.two > li.noted:nth-child(-n + 3) {
  background-color: tomato;
  border-bottom-color: seagreen;
}
```

#### Result

The first case applies a style to the first three list items with
`class="noted"` whether or not they are the first three items in the
list.

The second case applies a style to the items with `class="noted"` if
they are within the first 3 items in the list.

### Using of selector to fix striped tables

A common practice for tables is to use *zebra-stripes* which alternates
between light and dark background colors for rows, making tables easier
to read and more accessible. If a row is hidden, the stripes will appear
merged and alter the desired effect. In this example, you can see two
tables with a `hidden` row. The second table handles hidden rows using
`of :not([hidden])`.

#### HTML

[html]

```html
<table class="broken">
  <thead>
    <tr><th>Name</th><th>Age</th><th>Country</th></tr>
  </thead>
  <tbody>
    <tr><td>Mamitiana</td><td>23</td><td>Madagascar</td></tr>
    <tr><td>Yuki</td><td>48</td><td>Japan</td></tr>
    <tr hidden><td>Tlayolotl</td><td>36</td><td>Mexico</td></tr>
    <tr><td>Adilah</td><td>27</td><td>Morocco</td></tr>
    <tr><td>Vieno</td><td>55</td><td>Finland</td></tr>
    <tr><td>Ricardo</td><td>66</td><td>Brazil</td></tr>
  </tbody>
</table>
<table class="fixed">
  <thead>
    <tr><th>Name</th><th>Age</th><th>Country</th></tr>
  </thead>
  <tbody>
    <tr><td>Mamitiana</td><td>23</td><td>Madagascar</td></tr>
    <tr><td>Yuki</td><td>48</td><td>Japan</td></tr>
    <tr hidden><td>Tlayolotl</td><td>36</td><td>Mexico</td></tr>
    <tr><td>Adilah</td><td>27</td><td>Morocco</td></tr>
    <tr><td>Vieno</td><td>55</td><td>Finland</td></tr>
    <tr><td>Ricardo</td><td>66</td><td>Brazil</td></tr>
  </tbody>
</table>
```

#### CSS

[css]

```css
.broken > tbody > tr:nth-child(even) {
  background-color: silver;
}
```

[css]

```css
.fixed > tbody > tr:nth-child(even of :not([hidden])) {
  background-color: silver;
}
```

#### Result

In the first table this is just using `:nth-child(even)` the third row
has the `hidden` attribute applied to it. So in this instance the 3rd
row is not visible and the 2nd & 4th rows are counted as even, which
technically they are but visually they are not.

In the second table the *of syntax* is used to target only the `tr`s
that are **not** hidden using `:nth-child(even of :not([hidden]))`.

Specifications
--------------

  ----------------------------------------------------------------------------------

Specification
  ----------------------------------------------------------------------------------

  [Selectors Level 4\
  [\#
  nth-child-pseudo]](https://drafts.csswg.org/selectors/#nth-child-pseudo)

  ----------------------------------------------------------------------------------

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

`:nth-child`

1

12

3.5

9

9.5Before Opera 15, Opera does not handle dynamically inserted elements
for `:nth-child()`.

3.1

≤37

18

4

10.1Before Opera 15, Opera does not handle dynamically inserted elements
for `:nth-child()`.

2

1.0

`no_parent_required`

57

79

52

No

44

No

57

57

52

43

No

7.0

`of_syntax`

111

111

113

No

97

9

111

111

113

No

9

22.0

See also
--------

- [`:nth-of-type()`](:nth-of-type)
- [`:nth-last-child()`](:nth-last-child)
- [`:has()`](:has): pseudo-class for selecting parent element
- [](pseudo-classes.md#tree-structural_pseudo-classes)
- [CSS selectors](css_selectors.md) module

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child>
