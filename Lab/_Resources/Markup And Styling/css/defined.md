:defined
========

The `:defined` [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
[pseudo-class](pseudo-classes.md) represents any element that has been
defined. This includes any standard element built in to the browser, and
custom elements that have been successfully defined (i.e. with the
[`CustomElementRegistry.define()`](https://developer.mozilla.org/en-US/docs/Web/API/CustomElementRegistry/define)
method).

[css]

```css
/* Selects any defined element */
:defined {
  font-style: italic;
}

/* Selects any instance of a specific custom element */
simple-custom:defined {
  display: block;
}
```

Syntax
------

[css]

```css
:defined {
  /* ... */
}
```

Examples
--------

### Hiding elements until they are defined

The following snippets are taken from our
[defined-pseudo-class](https://github.com/mdn/web-components-examples/tree/main/defined-pseudo-class)
demo ([see it live
also](https://mdn.github.io/web-components-examples/defined-pseudo-class/)).

In this demo we define a very simple trivial custom element:

[js]

```js
customElements.define(
  "simple-custom",
  class extends HTMLElement {
    constructor() {
      super();

      let divElem = document.createElement("div");
      divElem.textContent = this.getAttribute("text");

      let shadowRoot = this.attachShadow().appendChild(divElem);
    }
  },
);
```

Then insert a copy of this element into the document, along with a
standard `<p>`:

[html]

```html
<simple-custom text="Custom element example text"></simple-custom>

<p>Standard paragraph example text</p>
```

In the CSS we first include the following rules:

[css]

```css
/* Give the two elements distinctive backgrounds */
p {
  background: yellow;
}

simple-custom {
  background: cyan;
}

/* Both the custom and the built-in element are given italic text */
:defined {
  font-style: italic;
}
```

Then provide the following two rules to hide any instances of our custom
element that are not defined, and display instances that are defined as
block level elements:

[css]

```css
simple-custom:not(:defined) {
  display: none;
}

simple-custom:defined {
  display: block;
}
```

This is useful if you have a complex custom element that takes a while
to load into the page --- you might want to hide instances of the
element until definition is complete, so that you don\'t end up with
flashes of ugly unstyled elements on the page

Specifications
--------------

  ----------------------------------------------------------------------------------------------------------

Specification
  ----------------------------------------------------------------------------------------------------------

  [HTML Standard\
  [\#
  selector-defined]](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-defined)

  ----------------------------------------------------------------------------------------------------------

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

`:defined`

54

79

63

No

41

10

54

54

63

41

10

6.0

See also
--------

- [Web
    components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/CSS/:defined>
