will-change
===========

The `will-change`
[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) property hints
to browsers how an element is expected to change. Browsers may set up
optimizations before an element is actually changed. These kinds of
optimizations can increase the responsiveness of a page by doing
potentially expensive work before they are actually required.

**Warning:** `will-change` is intended to be used as a last resort, in
order to try to deal with existing performance problems. It should not
be used to anticipate performance problems.

Proper usage of this property can be a bit tricky:

- *Don\'t apply will-change to too many elements.* The browser already
    tries as hard as it can to optimize everything. Some of the stronger
    optimizations that are likely to be tied to `will-change` end up
    using a lot of a machine\'s resources, and when overused like this
    can cause the page to slow down or consume a lot of resources.
- *Use sparingly.* The normal behavior for optimizations that the
    browser make is to remove the optimizations as soon as it can and
    revert back to normal. But adding `will-change` directly in a
    stylesheet implies that the targeted elements are always a few
    moments away from changing and the browser will keep the
    optimizations for much longer time than it would have otherwise. So
    it is a good practice to switch `will-change` on and off using
    script code before and after the change occurs.
- *Don\'t apply will-change to elements to perform premature
    optimization*. If your page is performing well, don\'t add the
    `will-change` property to elements just to wring out a little more
    speed. `will-change` is intended to be used as something of a last
    resort, in order to try to deal with existing performance problems.
    It should not be used to anticipate performance problems. Excessive
    use of `will-change` will result in excessive memory use and will
    cause more complex rendering to occur as the browser attempts to
    prepare for the possible change. This will lead to worse
    performance.
- *Give it sufficient time to work*. This property is intended as a
    method for authors to let the user-agent know about properties that
    are likely to change ahead of time. Then the browser can choose to
    apply any ahead-of-time optimizations required for the property
    change before the property change actually happens. So it is
    important to give the browser some time to actually do the
    optimizations. Find some way to predict at least slightly ahead of
    time that something will change, and set `will-change` then.
- *Be aware, that will-change may actually influence the visual
    appearance of elements*, when used with property values, that create
    a [](stacking_context.md)
    (e.g. will-change: opacity), as the stacking context is created up
    front.

Syntax
------

[css]

```css
/* Keyword values */
will-change: auto;
will-change: scroll-position;
will-change: contents;
will-change: transform; /* Example of <custom-ident> */
will-change: opacity; /* Example of <custom-ident> */
will-change: left, top; /* Example of two <animatable-feature> */

/* Global values */
will-change: inherit;
will-change: initial;
will-change: revert;
will-change: revert-layer;
will-change: unset;
```

### Values

[`auto`](#auto)

:   This keyword expresses no particular intent; the user agent should
    apply whatever heuristics and optimizations it normally does.

The `<animatable-feature>` can be one of the following values:

[`scroll-position`](#scroll-position)

:   Indicates that the author expects to animate or change the scroll
    position of the element in the near future.

[`contents`](#contents)

:   Indicates that the author expects to animate or change something
    about the element\'s contents in the near future.

[`<custom-ident>`](custom-ident.md)

:   Indicates that the author expects to animate or change the property
    with the given name on the element in the near future. If the
    property given is a shorthand, it indicates the expectation for all
    the longhands the shorthand expands to. It cannot be one of the
    following values: `unset`, `initial`, `inherit`, `will-change`,
    `auto`, `scroll-position`, or `contents`. The spec doesn\'t define
    the behavior of particular value, but it is common for `transform`
    to be a compositing layer hint. [Chrome currently takes two
    actions](https://github.com/operasoftware/devopera/pull/330), given
    particular CSS property idents: establish a new compositing layer or
    a new [stacking
    context](https://developer.mozilla.org/en-US/docs/Glossary/Stacking_context).

### Via stylesheet

It may be appropriate to include `will-change` in your style sheet for
an application that does page flips on key presses like an album or a
slide deck presentation where the pages are large and complex. This will
let browser prepare the transition ahead of time and allow for snappy
transitions between the pages as soon as the key is pressed. But use
caution with the `will-change` property directly in stylesheets. It may
cause the browser to keep the optimization in memory for much longer
than it is needed.

[css]

```css
.slide {
  will-change: transform;
}
```

Formal definition
-----------------

  ---------------------------------- --------------
  [Initial value](initial_value.md)     `auto`
  Applies to                         all elements
  [Inherited](inheritance.md)           no
  [Computed value](computed_value.md)   as specified
  Animation type                     discrete
  ---------------------------------- --------------

Formal syntax
-------------

```
will-change = 
  auto                    |
  <animateable-feature>#  

<animateable-feature> = 
  scroll-position  |
  contents         |
  <custom-ident>   
```

Examples
--------

### Via script

This is an example showing how to apply the `will-change` property
through scripting, which is probably what you should be doing in most
cases.

[js]

```js
const el = document.getElementById("element");

// Set will-change when the element is hovered
el.addEventListener("mouseenter", hintBrowser);
el.addEventListener("animationEnd", removeHint);

function hintBrowser() {
  // The optimizable properties that are going to change
  // in the animation's keyframes block
  this.style.willChange = "transform, opacity";
}

function removeHint() {
  this.style.willChange = "auto";
}
```

Specifications
--------------

  ------------------------------------------------------------------------------

Specification
  ------------------------------------------------------------------------------

  [CSS Will Change Module Level 1\
  [\#
  will-change]](https://drafts.csswg.org/css-will-change/#will-change)

  ------------------------------------------------------------------------------

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

`will-change`

36

79

36

No

24

9.1

37

36

36

24

9.3

3.0

See also
--------

- [`transform`](transform.md)
- Individual transform properties:
  - [`translate`](_Resources/Markup%20And%20Styling/css/translate.md)
  - [`scale`](_Resources/Markup%20And%20Styling/css/scale.md)
  - [`rotate`](_Resources/Markup%20And%20Styling/css/rotate.md)
  - Note: there is no individual `skew` property

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/will-change>
