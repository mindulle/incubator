\<embed\>: The Embed External Content element
=============================================

The `<embed>` [HTML](../index) element embeds external content at the
specified point in the document. This content is provided by an external
application or other source of interactive content such as a browser
plug-in.

Try it
------

**Note:** This topic documents only the element that is defined as part
of the [HTML Living
Standard](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-embed-element).
It does not address earlier, non-standardized implementation of the
element.

Keep in mind that most modern browsers have deprecated and removed
support for browser plug-ins, so relying upon `<embed>` is generally not
wise if you want your site to be operable on the average user\'s
browser.

Attributes
----------

This element\'s attributes include the [](_Resources/Markup%20And%20Styling/html/global_attributes/index.md).

[`height`](#height)

:   The displayed height of the resource, in [CSS
    pixels](https://drafts.csswg.org/css-values/#px). This must be an
    absolute value; percentages are *not* allowed.

[`src`](#src)

:   The URL of the resource being embedded.

[`type`](#type)

:   The [MIME
    type](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type)
    to use to select the plug-in to instantiate.

[`width`](#width)

:   The displayed width of the resource, in [CSS
    pixels](https://drafts.csswg.org/css-values/#px). This must be an
    absolute value; percentages are *not* allowed.

Usage notes
-----------

You can use the
[`object-position`](https://developer.mozilla.org/en-US/docs/Web/CSS/object-position)
property to adjust the positioning of the embedded object within the
element\'s frame, and the
[`object-fit`](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit)
property to control how the object\'s size is adjusted to fit within the
frame.

Examples
--------

[html]

```html
<embed
  type="video/quicktime"
  src="movie.mov"
  width="640"
  height="480"
  title="Title of my video" />
```

Accessibility concerns
----------------------

Use the [`title` attribute](../global_attributes/title) on an `embed`
element to label its content so that people navigating with assistive
technology such as a screen reader can understand what it contains. The
title\'s value should concisely describe the embedded content. Without a
title, they may not be able to determine what its embedded content is.
This context shift can be confusing and time-consuming, especially if
the `embed` element contains interactive content like video or audio.

Technical summary
-----------------

  --------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [Content categories](../content_categories)   [Flow content](../content_categories#flow_content), [phrasing content](../content_categories#phrasing_content), embedded content, interactive content, [palpable content](../content_categories#palpable_content).
  Permitted content                             None; it is a [void element](https://developer.mozilla.org/en-US/docs/Glossary/Void_element).
  Tag omission                                  Must have a start tag, and must not have an end tag.
  Permitted parents                             Any element that accepts embedded content.
  Implicit ARIA role                            [No corresponding role](https://www.w3.org/TR/html-aria/#dfn-no-corresponding-role)
  Permitted ARIA roles                          [`application`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/application_role), [`document`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/document_role), [`img`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/img_role), [`none`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/none_role), [`presentation`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/presentation_role)
  DOM interface                                 [`HTMLEmbedElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLEmbedElement)
  --------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Specifications
--------------

  ----------------------------------------------------------------------------------------------------------------

Specification
  ----------------------------------------------------------------------------------------------------------------

  [HTML Standard\
  [\#
  the-embed-element]](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-embed-element)

  ----------------------------------------------------------------------------------------------------------------

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

`embed`

1

12

1

Yes

≤12.1

≤4

4.4

18

4

≤12.1

≤3.2

1.0

`align`

1

79

1

No

≤12.1

≤4

4.4

18

4

≤12.1

≤3.2

1.0

`height`

1

12

1

≤6

≤12.1

≤4

4.4

18

4

≤12.1

≤3.2

1.0

`name`

1

12

1

≤6

≤12.1

≤4

4.4

18

4

≤12.1

≤3.2

1.0

`src`

1

12

1

≤6

≤12.1

≤4

4.4

18

4

≤12.1

≤3.2

1.0

`type`

1

79

1

No

≤12.1

≤4

4.4

18

4

≤12.1

≤3.2

1.0

`width`

1

12

1

≤6

≤12.1

≤4

4.4

18

4

≤12.1

≤3.2

1.0

See also
--------

- Other elements that are used for embedding content of various types
    include [`<audio>`](audio), [`<canvas>`](canvas),
    [`<iframe>`](iframe), [`<img>`](img), `<math>`,
    [`<object>`](object),
    [`<svg>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg),
    and [`<video>`](video).
- Positioning and sizing the embedded content within its frame:
    [`object-position`](https://developer.mozilla.org/en-US/docs/Web/CSS/object-position)
    and
    [`object-fit`](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed>>
