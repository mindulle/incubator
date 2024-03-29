CSS box alignment
=================

The **CSS box alignment** module specifies CSS features that relate to
the alignment of boxes in the various CSS box layout models: block
layout, table layout, flex layout, and grid layout. The module aims to
create a consistent method of alignment across all of CSS. This document
details the general concepts found in the specification.

**Note:** The documentation for each layout method will detail how Box
Alignment is applied there.

Older alignment methods
-----------------------

CSS traditionally had very limited alignment capabilities. We were able
to align text using [`text-align`](text-align.md), center blocks using auto
[`margin`](margin.md)s, and in table or inline-block layouts using the
[`vertical-align`](vertical-align.md) property. Alignment of text is now
covered by the [Inline Layout](https://www.w3.org/TR/css-inline-3/) and
[CSS Text](https://www.w3.org/TR/css-text-3/) modules, and for the first
time in Box Alignment we have full horizontal and vertical alignment
capabilities.

If you initially learned [Flexbox](css_flexible_box_layout.md) then you may
consider these properties to be part of the Flexbox specification, and
some of the properties are indeed listed in Level 1 of Flexbox. However
the specification notes that the Box Alignment specification should be
referred to as it may add additional capabilities over what is currently
in Flexbox.

Basic examples
--------------

The following examples demonstrate how some of the Box Alignment
Properties are applied in [Grid](css_grid_layout.md) and
[Flexbox](css_flexible_box_layout.md).

### CSS grid layout alignment example

In this example using Grid Layout, there is extra space in the grid
container after laying out the fixed width tracks on the inline (main)
axis. This space is distributed using
[`justify-content`](justify-content.md). On the block (cross) axis the
alignment of the items inside their grid areas is controlled with
[`align-items`](align-items.md). The first item overrides the `align-items`
value set on the group by setting [`align-self`](align-self.md) to
`center`.

### Flexbox Alignment Example

In this example, three flex items are aligned on the main axis using
`justify-content` and on the Cross Axis using `align-items`. The first
item overrides the `align-items` set on the group by setting
`align-self` to `center`.

Key concepts and terminology
----------------------------

The specification details some alignment terminology to make it easier
to discuss these alignment properties outside their implementation
within a particular layout method. There are also some key concepts
which are common to all layout methods.

### Relationship to writing modes

Alignment is linked to writing modes in that when we align an item we do
not consider whether we are aligning it to the physical dimensions of
top, right, bottom and left. Instead we describe alignment in terms of
the start and end of the particular dimension we are working with. This
ensures that alignment works in the same way whichever writing mode the
document has.

### Two dimensions of alignment

When using the box alignment properties you will align content on one of
two axes --- the inline (or main) axis, and the block (or cross) axis.
The inline axis is the axis along which words in a sentence flow in the
writing mode being used --- for English, for example, the inline axis is
horizontal. The block axis is the axis along which blocks, such as
paragraph elements, are laid out and it runs across the Inline axis.

When aligning items on the inline axis you will use the properties which
begin with `justify-`:

- [`justify-items`](justify-items.md)
- [`justify-self`](justify-self.md)
- [`justify-content`](justify-content.md)

When aligning items on the block axis you will use the properties that
begin `align-`:

- [`align-items`](align-items.md)
- [`align-self`](align-self.md)
- [`align-content`](align-content.md)

Flexbox adds an additional complication in that the above is true when
[`flex-direction`](flex-direction.md) is set to `row`. The properties are
swapped when flexbox is set to `column`. Therefore, when working with
flexbox it is easier to think about the main and cross axis rather than
inline and block. The `justify-` properties are always used to align on
the main axis, the `align-` properties on the cross axis.

### The alignment subject

The **alignment subject** is the thing that is being aligned. For
`justify-self` or `align-self`, or when setting these values as a group
with `justify-items` or `align-items`, this will be the margin box of
the element that this property is being used on. The `justify-content`
and `align-content` properties differ per layout method.

### The alignment container

The **alignment container** is the box the subject is being aligned
inside. This will typically be the alignment subject\'s containing
block. An alignment container may contain one or many alignment
subjects.

The below image shows an alignment container with two alignment subjects
inside.

### Fallback alignment

If you set an alignment that cannot be fulfilled, then the **fallback
alignment** will come into play and deal with the available space. This
fallback alignment is specified individually for each layout method and
detailed on the page for that method.

Types of alignment
------------------

There are three different types of alignment that the specification
details; these use keyword values.

- **Positional alignment**: specifying the position of an alignment
    subject with relation to its alignment container.
- **Baseline alignment**: These keywords define alignment as a
    relationship among the baselines of multiple alignment subjects
    within an alignment context.
- **Distributed alignment**: These keywords define alignment as a
    distribution of space among alignment subjects.

### Positional alignment keyword values

The following values are defined for positional alignment, and can be
used as values for content alignment with `justify-content` and
`align-content` and also for self alignment with `justify-self` and
`align-self`.

- `center`
- `start`
- `end`
- `self-start`
- `self-end`
- `flex-start` for Flexbox only
- `flex-end` for Flexbox only
- `left`
- `right`

Other than the physical values of `left` and `right`, which relate to
physical attributes of the screen, all of the other values are logical
values and relate to the writing mode of the content.

For example, when working in CSS Grid Layout, if you are working in
English and set `justify-content` to `start` this will move the items in
the inline dimension to the start, which will be the left as sentences
in English start on the left. If you were using Arabic, a right to left
language, then the same value of `start` would result in the items
moving to the right, as sentences in Arabic start on the right-hand side
of the page.

Both of these examples have `justify-content: start`, however the
location of start changes according to the writing mode.

![There are two boxes, each with 3 children of differing heights but similar widths. The first box has three children with the letters A, B, and C. These three boxes are all aligned to the left. The second box has
three children with arabic letters in them. Those three boxes are all aligned to the right.](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAd4AAABlBAMAAAARyp/yAAAALVBMVEXAwMCXl5f///8rKkheXXFrans7O1WhoaeurrK3t7lLSmKRkJp1dYR/f4yJiJM0Xi65AAACmklEQVR42u3cT2sTQRgG8Il2s7vpNrR48yT9BA1vuolbC4GkCJ4C2oN/DoWtVPASKPQgCoF4EE8LPeglEMih14XgSQ+FXEUKQbxW1IPfwu1EcWZ3RzbFpEP6vJeQObx5fkx2MpPDsJUZ1Gq2mkUUBi+8M/OuTrm4d/ofAi+88MIL7+XwMrnOhm7IQ1fSRv56z90AXnjh/U9ep50hrjWJ13yvsffroJLBa7Qm8C5QoK3XItrJ4D0M58RbpBehHLfL35ly3MHxXHjtE/Y8emmJcR/xXNfluNdqSu+H7Z8J75uPoey1fnwKNPAafNoWe2LcJzxXfVnydnoqb4HIbce9d8kLJO83oj0NvHmedKEkxDWrPNfwWPLm11TeUfkB1eJet05N0WuS13eDi/fuc69zS4i7uD4GNiVv4abK+71pUy/urdl+VfQWqGW4yxfvHfBZYI+FuBbtNu5tNe7IXqOifH6td79XeMF7yoYl0XvVY7YOz2/HbWxFOtHL+sRL9jolldfpU9LbZqNN0dsp67E+F8a2dTHuQZp3aUPlrXtf/F6Kd0P0Hnp6eE0/6bU/b59VKHmLqvm1osUq6T1l9YrozbsstxtqsN/octvD2P4ql9gu5KoKr0m9peT3ea87HvvTwKDbz6il7flo/yjuLe4ovLbv+rQW80ZDFIoN7GigrO95sO/FvY5yP3lAm6NS3PuansoNXhLd19c7rCTOg4Hy9+hV2vn3bbyB2db4vG+d4P8NeOGFF1544YUXXnjhhRdeeOGFF1544YUXXnjhhRfe1LjJmtCbrQG88MILL7zwwgsvvPDCq7s3U/3Le+4G8MILL7zwwgsvvPDCCy+88MILL7zwwjvFwv1m8MILL7waey/b/cC4/xneufH+Avyoc2BcIV5BAAAAAElFTkSuQmCC)

### Baseline alignment

The Baseline alignment keywords are used to align the baselines of boxes
across a group of alignment subjects. They can be used as values for
content alignment with `justify-content` and `align-content` and also
for self alignment with `justify-self` and `align-self`.

- `baseline`
- `first baseline`
- `last baseline`

Baseline content alignment --- specifying a baseline alignment value for
`justify-content` or `align-content` --- works in layout methods that
lay items out in rows. The alignment subjects are baseline aligned
against each other by adding padding inside the boxes.

Baseline self alignment shifts the boxes to align by baseline by adding
a margin outside the boxes. Self alignment is when using `justify-self`
or `align-self`, or when setting these values as a group with
`justify-items` and `align-items`.

### Distributed alignment

The **distributed alignment keywords** are used with the `align-content`
and `justify-content` properties. These keywords define what happens to
any additional space after alignment subjects have been displayed. The
values are as follows:

- `stretch`
- `space-between`
- `space-around`
- `space-evenly`

For example, in Flex Layout items are aligned with `flex-start`
initially. Working in a horizontal top to bottom writing mode such as
English, with `flex-direction` as `row` the items start on the far left
and any available space after displaying the items is placed after the
items.

![Three rectangles of different widths are inside a box. They are all aligned to the left side of the containing box, with about 10px between them, and 10px between the left side of the first rectangle and the
parent container](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAi8AAABkAgMAAAAzujhRAAAACVBMVEXY2NiXl5f///8iBAieAAAAlUlEQVRo3u3bMQ5AMBQG4BrcyxEMXMK9DHpKSTcUkZAU3z/+adJv6/BeQ19OugADcxkzxEIywsDAwMDAwJxipt1XPUlXXcx0uSOfwDQhnyph2kVXx223Sg0DAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3Mn5njInsP8ZOJ/kjtusrICAwMDAwMD8xzGXxWYF2NmSJ2/a8FPB9AAAAAASUVORK5CYII=)

If you set `justify-content: space-between` on the flex container, the
available space is now shared out and placed between the items.

There needs to be space available in the dimension you wish to align the
items in, in order for these keywords to take effect. With no space,
there is nothing to distribute.

Overflow alignment
------------------

The `safe` and `unsafe` keywords help define behavior when an alignment
subject is larger than the alignment container. The `safe` keyword will
align to `start` in the case of a specified alignment causing an
overflow, the aim being to avoid \"data loss\" where part of the item is
outside the boundaries of the alignment container and can\'t be scrolled
to.

If you specify `unsafe` then the alignment will be honoured even if it
would cause such data loss.

Gaps between boxes
------------------

The box alignment specification also includes the `gap`, `row-gap`, and
`column-gap` properties. These properties enable the setting of a
consistent gap between items in a row or column, in any layout method
which has items arranged in this way.

The `gap` property is a shorthand for `row-gap` and `column-gap`, which
allows us to set these properties at once:

- [`row-gap`](row-gap.md)
- [`column-gap`](column-gap.md)
- [`gap`](gap.md)

In the below example, a grid layout uses the `gap` shorthand to set a
`10px` gap between row tracks, and a `2em` gap between column tracks.

**Note:** The early grid implementation included `-gap` properties
prefixed with `grid-`. All browsers now support the unprefixed
properties, though you may see the following legacy properties in
examples and tutorials: [`grid-row-gap`](row-gap.md),
[`grid-column-gap`](column-gap.md), and [`grid-gap`](gap.md). The prefixed
versions will be maintained as an alias of the unprefixed ones.

Be aware that other things may increase the visual gap displayed, for
example using the space distribution keywords or adding margins to
items.

Pages detailing individual alignment properties
-----------------------------------------------

As the CSS box alignment properties are implemented differently
depending on the specification they interact with, refer to the
following pages for each layout type for details of how to use the
alignment properties with it:

- [](box_alignment_in_flexbox.md)
- [](_Resources/Markup%20And%20Styling/css/css_box_alignment/box_alignment_in_grid_layout.md)
- [](box_alignment_in_multi-column_layout.md)
- [](box_alignment_in_block_abspos_tables.md)

Reference
---------

### CSS Properties

- [`justify-content`](justify-content.md)
- [`align-content`](align-content.md)
- [`place-content`](place-content.md)
- [`justify-items`](justify-items.md)
- [`align-items`](align-items.md)
- [`place-items`](place-items.md)
- [`justify-self`](justify-self.md)
- [`align-self`](align-self.md)
- [`place-self`](place-self.md)
- [`row-gap`](row-gap.md)
- [`column-gap`](column-gap.md)
- [`gap`](gap.md)

### Glossary Entries

- [Cross
    axis](https://developer.mozilla.org/en-US/docs/Glossary/Cross_Axis)
- [Main
    axis](https://developer.mozilla.org/en-US/docs/Glossary/Main_Axis)
- [Alignment
    container](https://developer.mozilla.org/en-US/docs/Glossary/Alignment_Container)
- [Alignment
    subject](https://developer.mozilla.org/en-US/docs/Glossary/Alignment_Subject)
- [Fallback
    alignment](https://developer.mozilla.org/en-US/docs/Glossary/Fallback_Alignment)

Guides
------

- CSS Flexbox guide: *[](basic_concepts_of_flexbox.md)*
- CSS Flexbox guide: *[](aligning_items_in_a_flex_container.md)*
- CSS Grid guide: *[](_Resources/Markup%20And%20Styling/css/css_grid_layout/box_alignment_in_grid_layout.md)*

External Resources
------------------

- [CSS Grid, Flexbox and Box
    alignment](https://www.smashingmagazine.com/2016/11/css-grids-flexbox-box-alignment-new-layout-standard/)
- [Thoughts on partial implementations of Box
    alignment](https://blogs.igalia.com/jfernandez/2017/05/03/can-i-use-css-box-alignment/)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_box_alignment>
