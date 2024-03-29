Comments
========

A CSS **comment** is used to add explanatory notes to the code or to
prevent the browser from interpreting specific parts of the style sheet.
By design, comments have no effect on the layout of a document.

Syntax
------

Comments can be placed wherever white space is allowed within a style
sheet. They can be used on a single line, or traverse multiple lines.

[css]

```css
/* Comment */
```

Examples
--------

[css]

```css
/* A one-line comment */

/*
A comment
which stretches
over several
lines
*/

/* The comment below is used to
   disable specific styling */
/*
span {
  color: blue;
  font-size: 1.5em;
}
*/
```

Notes
-----

The `/* */` comment syntax is used for both single and multiline
comments. There is no other way to specify comments in external style
sheets. However, when using the
[`<style>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/style)
element, you may use `<!-- -->` to hide CSS from older browsers,
although this is not recommended. As with most programming languages
that use the `/* */` comment syntax, comments cannot be nested. In other
words, the first instance of `*/` that follows an instance of `/*`
closes the comment.

Specifications
--------------

- [CSS 2.1 Syntax and basic data types
    \#comments](https://www.w3.org/TR/CSS21/syndata.html#comments)

See also
--------

- CSS key concepts:
  - [CSS syntax](_Resources/Markup%20And%20Styling/css/syntax.md)
  - [At-rules](at-rule.md)
  - [Specificity](specificity.md)
  - [Inheritance](inheritance.md)
  - [Box model](introduction_to_the_css_box_model.md)
  - [Layout modes](layout_mode.md)
  - [Visual formatting models](visual_formatting_model.md)
  - [Margin collapsing](mastering_margin_collapsing.md)
  - Values
    - [Initial values](initial_value.md)
    - [Computed values](computed_value.md)
    - [Used values](used_value.md)
    - [Actual values](actual_value.md)
  - [Value definition syntax](value_definition_syntax.md)
  - [Shorthand properties](shorthand_properties.md)
  - [Replaced elements](replaced_element.md)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/Comments>
