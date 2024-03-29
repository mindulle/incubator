view-timeline
=============

**Experimental:** **This is an [experimental
technology](https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines/Experimental_deprecated_obsolete#experimental)**\
Check the [Browser compatibility table](#browser_compatibility)
carefully before using this in production.

The `view-timeline`
[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) [](shorthand_properties.md) is used to define a *named view progress
timeline*, which is progressed through based on the change in visibility
of an element (known as the *subject*) inside a scrollable element
(*scroller*). `view-timeline` is set on the subject.

The visibility of the subject inside the scroller is tracked --- by
default, the timeline is at 0% when the subject is first visible at one
edge of the scroller and 100% when it reaches the opposite edge.

`view-timeline` can contain two constituent values --- a name for the
named view progress timeline and an optional scroll axis value. The name
is then referenced in an [`animation-timeline`](animation-timeline.md)
declaration to indicate the element that will be animated as the
timeline progresses. This can be the subject element, but it doesn\'t
have to be --- you can animate a different element as the subject moves
through the scrolling area.

**Note:** If the scroller does not overflow its container in the axis
dimension or if the overflow is hidden or clipped, no timeline will be
created.

Constituent properties
----------------------

This property is a shorthand for the following CSS properties:

- [`view-timeline-name`](view-timeline-name.md)
- [`view-timeline-axis`](view-timeline-axis.md)

Syntax
------

[css]

```css
/* two values: one each for view-timeline-name and view-timeline-axis */
view-timeline: --custom_name_for_timeline block;
view-timeline: --custom_name_for_timeline inline;
view-timeline: --custom_name_for_timeline y;
view-timeline: --custom_name_for_timeline x;
view-timeline: none block;
view-timeline: none inline;
view-timeline: none y;
view-timeline: none x;

/* one value: view-timeline-name */
view-timeline: none;
view-timeline: --custom_name_for_timeline;
```

The `view-timeline` shorthand property can be applied to a container
element as a combination of the `<view-timeline-name>` and
`<view-timeline-axis>` values. At least one of the values must be
specified. If both the values are specified, the order followed must be
the `<view-timeline-name>` value followed by the `<view-timeline-axis>`
value.

**Note:** `<view-timeline-name>`s must be
[`<dashed-ident>`](dashed-ident.md) values, which means they must start
with `--`. This helps avoid name clashes with standard CSS keywords.

### Values

[`<view-timeline-name>`](#view-timeline-name)

:   See [`view-timeline-name`](view-timeline-name.md).

[`<view-timeline-axis>`](#view-timeline-axis)

:   See [`view-timeline-axis`](view-timeline-axis.md). The default value is
    `block`.

Formal definition
-----------------

+-----------------------------------+-----------------------------------+
| [Initial value](initial_value.md)    | as each of the properties of the  |
|                                   | shorthand:\                       |
|                                   |                                   |
|                                   | -   [](view-timeline-name.md): |
|                                   |     `none`                        |
|                                   | -   [](view-timeline-axis.md): |
|                                   |     `block`                       |
+-----------------------------------+-----------------------------------+
| Applies to                        | all elements                      |
+-----------------------------------+-----------------------------------+
| [Inherited](inheritance.md)          | no                                |
+-----------------------------------+-----------------------------------+
| [Computed value](computed_value.md)  | as each of the properties of the  |
|                                   | shorthand:\                       |
|                                   |                                   |
|                                   | -   [](view-timeline-name.md): |
|                                   |     `none` or an ordered list of  |
|                                   |     identifiers                   |
|                                   | -   [](view-timeline-axis.md): |
|                                   |     as specified                  |
+-----------------------------------+-----------------------------------+
| Animation type                    | as each of the properties of the  |
|                                   | shorthand:\                       |
|                                   |                                   |
|                                   | -   [](view-timeline-name.md): |
|                                   |     Not animatable                |
|                                   | -   [](view-timeline-axis.md): |
|                                   |     Not animatable                |
+-----------------------------------+-----------------------------------+

Formal syntax
-------------

```
view-timeline = 
  [ <'view-timeline-name'> || <'view-timeline-axis'> ]#  
```

Examples
--------

### Creating a named view progress timeline

A view progress timeline named `--subjectReveal` is defined using the
`view-timeline` property on a subject element with a `class` of
`animation`. This is then set as the timeline for the same element using
`animation-timeline: --subjectReveal`. The result is that the subject
element animates as it moves upwards through the document as it is
scrolled.

#### HTML

The HTML for the example is shown below.

[html]

```html
<div class="content">
  <h1>Content</h1>

  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua. Risus quis varius quam
    quisque id. Et ligula ullamcorper malesuada proin libero nunc consequat
    interdum varius. Elit ullamcorper dignissim cras tincidunt lobortis feugiat
    vivamus at augue.
  </p>

  <p>
    Dolor sed viverra ipsum nunc aliquet. Sed sed risus pretium quam vulputate
    dignissim. Tortor aliquam nulla facilisi cras. A erat nam at lectus urna
    duis convallis convallis. Nibh ipsum consequat nisl vel pretium lectus.
    Sagittis aliquam malesuada bibendum arcu vitae elementum. Malesuada bibendum
    arcu vitae elementum curabitur vitae nunc sed velit.
  </p>

  <div class="subject animation"></div>

  <p>
    Adipiscing enim eu turpis egestas pretium aenean pharetra magna ac. Arcu
    cursus vitae congue mauris rhoncus aenean vel. Sit amet cursus sit amet
    dictum. Augue neque gravida in fermentum et. Gravida rutrum quisque non
    tellus orci ac auctor augue mauris. Risus quis varius quam quisque id diam
    vel quam elementum. Nibh praesent tristique magna sit amet purus gravida
    quis. Duis ultricies lacus sed turpis tincidunt id aliquet. In egestas erat
    imperdiet sed euismod nisi. Eget egestas purus viverra accumsan in nisl nisi
    scelerisque. Netus et malesuada fames ac.
  </p>
</div>
```

#### CSS

The `subject` element and its containing `content` element are styled
minimally, and the text content is given some basic font settings:

[css]

```css
.subject {
  width: 300px;
  height: 200px;
  margin: 0 auto;
  background-color: deeppink;
}

.content {
  width: 75%;
  max-width: 800px;
  margin: 0 auto;
}

p,
h1 {
  font-family: Arial, Helvetica, sans-serif;
}

h1 {
  font-size: 3rem;
}

p {
  font-size: 1.5rem;
  line-height: 1.5;
}
```

The `<div>` with the class of `subject` is also given a class of
`animation` --- this is where `view-timeline` is set to define a named
view progress timeline. It is also given an `animation-timeline` name
with the same value to declare that this will be the element animated as
the view progress timeline is progressed.

Last, an animation is specified on the element that animates its opacity
and scale, causing it to fade in and size up as it moves up the
scroller.

[css]

```css
.animation {
  view-timeline: --subjectReveal block;
  animation-timeline: --subjectReveal;

  animation-name: appear;
  animation-fill-mode: both;
  animation-duration: 1ms; /* Firefox requires this to apply the animation */
}

@keyframes appear {
  from {
    opacity: 0;
    transform: scaleX(0);
  }

  to {
    opacity: 1,
    transform: scaleX(1);
  }
}
```

#### Result

Scroll to see the subject element being animated.

Specifications
--------------

  --------------------------------------------------------------------------------------------------------

Specification
  --------------------------------------------------------------------------------------------------------

  [Scroll-driven Animations\
  [\#
  view-timeline-shorthand]](https://drafts.csswg.org/scroll-animations/#view-timeline-shorthand)

  --------------------------------------------------------------------------------------------------------

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

`view-timeline`

115`view-timeline-attachment` not included in shorthand.

115`view-timeline-attachment` not included in shorthand.

114Now supports the `x` and `y` values, and also the deprecated
`horizontal` and `vertical` values.

No

101`view-timeline-attachment` not included in shorthand.

No

115`view-timeline-attachment` not included in shorthand.

115`view-timeline-attachment` not included in shorthand.

No

No`view-timeline-attachment` not included in shorthand.

No

No`view-timeline-attachment` not included in shorthand.

See also
--------

- [`animation-timeline`](animation-timeline.md)
- [`timeline-scope`](timeline-scope.md)
- [`view-timeline-axis`](view-timeline-axis.md),
    [`view-timeline-name`](view-timeline-name.md)
- [CSS scroll-driven animations](css_scroll-driven_animations.md)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/view-timeline>
