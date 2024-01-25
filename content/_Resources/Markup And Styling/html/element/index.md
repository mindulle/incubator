HTML elements reference
=======================

This page lists all the
[HTML](https://developer.mozilla.org/en-US/docs/Glossary/HTML)
[elements](https://developer.mozilla.org/en-US/docs/Glossary/Element),
which are created using
[tags](https://developer.mozilla.org/en-US/docs/Glossary/Tag).

They are grouped by function to help you find what you have in mind
easily. An alphabetical list of all elements is provided in the sidebar
on every element\'s page as well as this one.

**Note:** For more information about the basics of HTML elements and
attributes, see [the section on elements in the Introduction to HTML
article](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML#elements_%e2%80%94_the_basic_building_blocks).

Main root
---------

  Element                    Description
  -------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<html>`](element/html)   Represents the root (top-level element) of an HTML document, so it is also referred to as the *root element*. All other elements must be descendants of this element.

Document metadata
-----------------

Metadata contains information about the page. This includes information
about styles, scripts and data to help software ([search
engines](https://developer.mozilla.org/en-US/docs/Glossary/Search_engine),
[browsers](https://developer.mozilla.org/en-US/docs/Glossary/Browser),
etc.) use and render the page. Metadata for styles and scripts may be
defined in the page or linked to another file that has the information.

  Element                      Description
  ---------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<base>`](element/base)     Specifies the base URL to use for all relative URLs in a document. There can be only one such element in a document.
  [`<head>`](element/head)     Contains machine-readable information (metadata) about the document, like its [title](element/title), [scripts](element/script), and [style sheets](element/style).
  [`<link>`](element/link)     Specifies relationships between the current document and an external resource. This element is most commonly used to link to CSS but is also used to establish site icons (both \"favicon\" style icons and icons for the home screen and apps on mobile devices) among other things.
  [`<meta>`](element/meta)     Represents [metadata](https://developer.mozilla.org/en-US/docs/Glossary/Metadata) that cannot be represented by other HTML meta-related elements, like [`<base>`](element/base), [`<link>`](element/link), [`<script>`](element/script), [`<style>`](element/style) and [`<title>`](element/title).
  [`<style>`](element/style)   Contains style information for a document or part of a document. It contains CSS, which is applied to the contents of the document containing this element.
  [`<title>`](element/title)   Defines the document\'s title that is shown in a [browser](https://developer.mozilla.org/en-US/docs/Glossary/Browser)\'s title bar or a page\'s tab. It only contains text; tags within the element are ignored.

Sectioning root
---------------

  Element                    Description
  -------------------------- -----------------------------------------------------------------------------------------------
  [`<body>`](element/body)   represents the content of an HTML document. There can be only one such element in a document.

Content sectioning
------------------

Content sectioning elements allow you to organize the document content
into logical pieces. Use the sectioning elements to create a broad
outline for your page content, including header and footer navigation,
and heading elements to identify sections of content.

  Element                                                                                                                                                                                                                  Description
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<address>`](element/address)                                                                                                                                                                                           Indicates that the enclosed HTML provides contact information for a person or people, or for an organization.
  [`<article>`](element/article)                                                                                                                                                                                           Represents a self-contained composition in a document, page, application, or site, which is intended to be independently distributable or reusable (e.g., in syndication). Examples include a forum post, a magazine or newspaper article, a blog entry, a product card, a user-submitted comment, an interactive widget or gadget, or any other independent item of content.
  [`<aside>`](element/aside)                                                                                                                                                                                               Represents a portion of a document whose content is only indirectly related to the document\'s main content. Asides are frequently presented as sidebars or call-out boxes.
  [`<footer>`](element/footer)                                                                                                                                                                                             Represents a footer for its nearest ancestor [sectioning content](content_categories#sectioning_content) or [sectioning root](element/heading_elements) element. A `<footer>` typically contains information about the author of the section, copyright data, or links to related documents.
  [`<header>`](element/header)                                                                                                                                                                                             Represents introductory content, typically a group of introductory or navigational aids. It may contain some heading elements but also a logo, a search form, an author name, and other elements.
  [`<h1>`](element/heading_elements), [`<h2>`](element/heading_elements), [`<h3>`](element/heading_elements), [`<h4>`](element/heading_elements), [`<h5>`](element/heading_elements), [`<h6>`](element/heading_elements)   Represent six levels of section headings. `<h1>` is the highest section level and `<h6>` is the lowest.
  [`<hgroup>`](element/hgroup)                                                                                                                                                                                             Represents a heading grouped with any secondary content, such as subheadings, an alternative title, or a tagline.
  [`<main>`](element/main)                                                                                                                                                                                                 Represents the dominant content of the body of a document. The main content area consists of content that is directly related to or expands upon the central topic of a document, or the central functionality of an application.
  [`<nav>`](element/nav)                                                                                                                                                                                                   Represents a section of a page whose purpose is to provide navigation links, either within the current document or to other documents. Common examples of navigation sections are menus, tables of contents, and indexes.
  [`<section>`](element/section)                                                                                                                                                                                           Represents a generic standalone section of a document, which doesn\'t have a more specific semantic element to represent it. Sections should always have a heading, with very few exceptions.
  [`<search>`](element/search)                                                                                                                                                                                             Represents a part that contains a set of form controls or other content related to performing a search or filtering operation.

Text content
------------

Use HTML text content elements to organize blocks or sections of content
placed between the opening [`<body>`](element/body) and closing
`</body>` tags. Important for
[accessibility](https://developer.mozilla.org/en-US/docs/Glossary/Accessibility)
and [SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO), these
elements identify the purpose or structure of that content.

  Element                                Description
  -------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<blockquote>`](element/blockquote)   Indicates that the enclosed text is an extended quotation. Usually, this is rendered visually by indentation. A URL for the source of the quotation may be given using the `cite` attribute, while a text representation of the source can be given using the [`<cite>`](element/cite) element.
  [`<dd>`](element/dd)                   Provides the description, definition, or value for the preceding term ([`<dt>`](element/dt)) in a description list ([`<dl>`](element/dl)).
  [`<div>`](element/div)                 The generic container for flow content. It has no effect on the content or layout until styled in some way using CSS (e.g., styling is directly applied to it, or some kind of layout model like [flexbox](https://developer.mozilla.org/en-US/docs/Glossary/Flexbox) is applied to its parent element).
  [`<dl>`](element/dl)                   Represents a description list. The element encloses a list of groups of terms (specified using the [`<dt>`](element/dt) element) and descriptions (provided by [`<dd>`](element/dd) elements). Common uses for this element are to implement a glossary or to display metadata (a list of key-value pairs).
  [`<dt>`](element/dt)                   Specifies a term in a description or definition list, and as such must be used inside a [`<dl>`](element/dl) element. It is usually followed by a [`<dd>`](element/dd) element; however, multiple `<dt>` elements in a row indicate several terms that are all defined by the immediate next [`<dd>`](element/dd) element.
  [`<figcaption>`](element/figcaption)   Represents a caption or legend describing the rest of the contents of its parent [`<figure>`](element/figure) element.
  [`<figure>`](element/figure)           Represents self-contained content, potentially with an optional caption, which is specified using the [`<figcaption>`](element/figcaption) element. The figure, its caption, and its contents are referenced as a single unit.
  [`<hr>`](element/hr)                   Represents a thematic break between paragraph-level elements: for example, a change of scene in a story, or a shift of topic within a section.
  [`<li>`](element/li)                   Represents an item in a list. It must be contained in a parent element: an ordered list ([`<ol>`](element/ol)), an unordered list ([`<ul>`](element/ul)), or a menu ([`<menu>`](element/menu)). In menus and unordered lists, list items are usually displayed using bullet points. In ordered lists, they are usually displayed with an ascending counter on the left, such as a number or letter.
  [`<menu>`](element/menu)               A semantic alternative to [`<ul>`](element/ul), but treated by browsers (and exposed through the accessibility tree) as no different than [`<ul>`](element/ul). It represents an unordered list of items (which are represented by [`<li>`](element/li) elements).
  [`<ol>`](element/ol)                   Represents an ordered list of items --- typically rendered as a numbered list.
  [`<p>`](element/p)                     Represents a paragraph. Paragraphs are usually represented in visual media as blocks of text separated from adjacent blocks by blank lines and/or first-line indentation, but HTML paragraphs can be any structural grouping of related content, such as images or form fields.
  [`<pre>`](element/pre)                 Represents preformatted text which is to be presented exactly as written in the HTML file. The text is typically rendered using a non-proportional, or [monospaced](https://en.wikipedia.org/wiki/Monospaced_font), font. Whitespace inside this element is displayed as written.
  [`<ul>`](element/ul)                   Represents an unordered list of items, typically rendered as a bulleted list.

Inline text semantics
---------------------

Use the HTML inline text semantic to define the meaning, structure, or
style of a word, line, or any arbitrary piece of text.

  Element                        Description
  ------------------------------ ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<a>`](element/a)             Together with its `href` attribute, creates a hyperlink to web pages, files, email addresses, locations within the current page, or anything else a URL can address.
  [`<abbr>`](element/abbr)       Represents an abbreviation or acronym.
  [`<b>`](element/b)             Used to draw the reader\'s attention to the element\'s contents, which are not otherwise granted special importance. This was formerly known as the Boldface element, and most browsers still draw the text in boldface. However, you should not use `<b>` for styling text or granting importance. If you wish to create boldface text, you should use the CSS [`font-weight`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight) property. If you wish to indicate an element is of special importance, you should use the strong element.
  [`<bdi>`](element/bdi)         Tells the browser\'s bidirectional algorithm to treat the text it contains in isolation from its surrounding text. It\'s particularly useful when a website dynamically inserts some text and doesn\'t know the directionality of the text being inserted.
  [`<bdo>`](element/bdo)         Overrides the current directionality of text, so that the text within is rendered in a different direction.
  [`<br>`](element/br)           Produces a line break in text (carriage-return). It is useful for writing a poem or an address, where the division of lines is significant.
  [`<cite>`](element/cite)       Used to mark up the title of a cited creative work. The reference may be in an abbreviated form according to context-appropriate conventions related to citation metadata.
  [`<code>`](element/code)       Displays its contents styled in a fashion intended to indicate that the text is a short fragment of computer code. By default, the content text is displayed using the user agent\'s default monospace font.
  [`<data>`](element/data)       Links a given piece of content with a machine-readable translation. If the content is time- or date-related, the`<time>` element must be used.
  [`<dfn>`](element/dfn)         Used to indicate the term being defined within the context of a definition phrase or sentence. The ancestor [`<p>`](element/p) element, the [`<dt>`](element/dt)/[`<dd>`](element/dd) pairing, or the nearest section ancestor of the `<dfn>` element, is considered to be the definition of the term.
  [`<em>`](element/em)           Marks text that has stress emphasis. The `<em>` element can be nested, with each nesting level indicating a greater degree of emphasis.
  [`<i>`](element/i)             Represents a range of text that is set off from the normal text for some reason, such as idiomatic text, technical terms, and taxonomical designations, among others. Historically, these have been presented using italicized type, which is the original source of the `<i>` naming of this element.
  [`<kbd>`](element/kbd)         Represents a span of inline text denoting textual user input from a keyboard, voice input, or any other text entry device. By convention, the user agent defaults to rendering the contents of a `<kbd>` element using its default monospace font, although this is not mandated by the HTML standard.
  [`<mark>`](element/mark)       Represents text which is marked or highlighted for reference or notation purposes due to the marked passage\'s relevance in the enclosing context.
  [`<q>`](element/q)             Indicates that the enclosed text is a short inline quotation. Most modern browsers implement this by surrounding the text in quotation marks. This element is intended for short quotations that don\'t require paragraph breaks; for long quotations use the [`<blockquote>`](element/blockquote) element.
  [`<rp>`](element/rp)           Used to provide fall-back parentheses for browsers that do not support the display of ruby annotations using the [`<ruby>`](element/ruby) element. One `<rp>` element should enclose each of the opening and closing parentheses that wrap the [`<rt>`](element/rt) element that contains the annotation\'s text.
  [`<rt>`](element/rt)           Specifies the ruby text component of a ruby annotation, which is used to provide pronunciation, translation, or transliteration information for East Asian typography. The `<rt>` element must always be contained within a [`<ruby>`](element/ruby) element.
  [`<ruby>`](element/ruby)       Represents small annotations that are rendered above, below, or next to base text, usually used for showing the pronunciation of East Asian characters. It can also be used for annotating other kinds of text, but this usage is less common.
  [`<s>`](element/s)             Renders text with a strikethrough, or a line through it. Use the `<s>` element to represent things that are no longer relevant or no longer accurate. However, `<s>` is not appropriate when indicating document edits; for that, use the del and ins elements, as appropriate.
  [`<samp>`](element/samp)       Used to enclose inline text which represents sample (or quoted) output from a computer program. Its contents are typically rendered using the browser\'s default monospaced font (such as [Courier](https://en.wikipedia.org/wiki/Courier_(typeface)) or Lucida Console).
  [`<small>`](element/small)     Represents side-comments and small print, like copyright and legal text, independent of its styled presentation. By default, it renders text within it one font size smaller, such as from `small` to `x-small`.
  [`<span>`](element/span)       A generic inline container for phrasing content, which does not inherently represent anything. It can be used to group elements for styling purposes (using the `class` or `id` attributes), or because they share attribute values, such as `lang`. It should be used only when no other semantic element is appropriate. `<span>` is very much like a div element, but div is a [block-level element](https://developer.mozilla.org/en-US/docs/Glossary/Block-level_content) whereas a `<span>` is an [inline-level element](https://developer.mozilla.org/en-US/docs/Glossary/Inline-level_content).
  [`<strong>`](element/strong)   Indicates that its contents have strong importance, seriousness, or urgency. Browsers typically render the contents in bold type.
  [`<sub>`](element/sub)         Specifies inline text which should be displayed as subscript for solely typographical reasons. Subscripts are typically rendered with a lowered baseline using smaller text.
  [`<sup>`](element/sup)         Specifies inline text which is to be displayed as superscript for solely typographical reasons. Superscripts are usually rendered with a raised baseline using smaller text.
  [`<time>`](element/time)       Represents a specific period in time. It may include the `datetime` attribute to translate dates into machine-readable format, allowing for better search engine results or custom features such as reminders.
  [`<u>`](element/u)             Represents a span of inline text which should be rendered in a way that indicates that it has a non-textual annotation. This is rendered by default as a simple solid underline but may be altered using CSS.
  [`<var>`](element/var)         Represents the name of a variable in a mathematical expression or a programming context. It\'s typically presented using an italicized version of the current typeface, although that behavior is browser-dependent.
  [`<wbr>`](element/wbr)         Represents a word break opportunity---a position within text where the browser may optionally break a line, though its line-breaking rules would not otherwise create a break at that location.

Image and multimedia
--------------------

HTML supports various multimedia resources such as images, audio, and
video.

  Element                      Description
  ---------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<area>`](element/area)     Defines an area inside an image map that has predefined clickable areas. An *image map* allows geometric areas on an image to be associated with [hyperlink](https://developer.mozilla.org/en-US/docs/Glossary/Hyperlink).
  [`<audio>`](element/audio)   Used to embed sound content in documents. It may contain one or more audio sources, represented using the `src` attribute or the source element: the browser will choose the most suitable one. It can also be the destination for streamed media, using a [`MediaStream`](https://developer.mozilla.org/en-US/docs/Web/API/MediaStream).
  [`<img>`](element/img)       Embeds an image into the document.
  [`<map>`](element/map)       Used with [`<area>`](element/area) elements to define an image map (a clickable link area).
  [`<track>`](element/track)   Used as a child of the media elements, audio and video. It lets you specify timed text tracks (or time-based data), for example to automatically handle subtitles. The tracks are formatted in [WebVTT format](https://developer.mozilla.org/en-US/docs/Web/API/WebVTT_API) (`.vtt` files)---Web Video Text Tracks.
  [`<video>`](element/video)   Embeds a media player which supports video playback into the document. You can also use `<video>` for audio content, but the audio element may provide a more appropriate user experience.

Embedded content
----------------

In addition to regular multimedia content, HTML can include a variety of
other content, even if it\'s not always easy to interact with.

  Element                          Description
  -------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<embed>`](element/embed)       Embeds external content at the specified point in the document. This content is provided by an external application or other source of interactive content such as a browser plug-in.
  [`<iframe>`](element/iframe)     Represents a nested browsing context, embedding another HTML page into the current one.
  [`<object>`](element/object)     Represents an external resource, which can be treated as an image, a nested browsing context, or a resource to be handled by a plugin.
  [`<picture>`](element/picture)   Contains zero or more [`<source>`](element/source) elements and one [`<img>`](element/img) element to offer alternative versions of an image for different display/device scenarios.
  [`<portal>`](element/portal)     Enables the embedding of another HTML page into the current one to enable smoother navigation into new pages.
  [`<source>`](element/source)     Specifies multiple media resources for the picture, the audio element, or the video element. It is a void element, meaning that it has no content and does not have a closing tag. It is commonly used to offer the same media content in multiple file formats in order to provide compatibility with a broad range of browsers given their differing support for [image file formats](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types) and [media file formats](https://developer.mozilla.org/en-US/docs/Web/Media/Formats).

SVG and MathML
--------------

You can embed [SVG](https://developer.mozilla.org/en-US/docs/Web/SVG)
and [MathML](https://developer.mozilla.org/en-US/docs/Web/MathML)
content directly into HTML documents, using the
[`<svg>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg)
and `<math>` elements.

  Element                                                                   Description
  ------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<svg>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg)   Container defining a new coordinate system and [viewport](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/viewBox). It is used as the outermost element of SVG documents, but it can also be used to embed an SVG fragment inside an SVG or HTML document.
  `<math>`                                                                  The top-level element in MathML. Every valid MathML instance must be wrapped in it. In addition, you must not nest a second `<math>` element in another, but you can have an arbitrary number of other child elements in it.

Scripting
---------

To create dynamic content and Web applications, HTML supports the use of
scripting languages, most prominently JavaScript. Certain elements
support this capability.

  Element                            Description
  ---------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<canvas>`](element/canvas)       Container element to use with either the [canvas scripting API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API) or the [WebGL API](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) to draw graphics and animations.
  [`<noscript>`](element/noscript)   Defines a section of HTML to be inserted if a script type on the page is unsupported or if scripting is currently turned off in the browser.
  [`<script>`](element/script)       Used to embed executable code or data; this is typically used to embed or refer to JavaScript code. The `<script>` element can also be used with other languages, such as [WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)\'s GLSL shader programming language and [JSON](https://developer.mozilla.org/en-US/docs/Glossary/JSON).

Demarcating edits
-----------------

These elements let you provide indications that specific parts of the
text have been altered.

  Element                  Description
  ------------------------ -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<del>`](element/del)   Represents a range of text that has been deleted from a document. This can be used when rendering \"track changes\" or source code diff information, for example. The `<ins>` element can be used for the opposite purpose: to indicate text that has been added to the document.
  [`<ins>`](element/ins)   Represents a range of text that has been added to a document. You can use the `<del>` element to similarly represent a range of text that has been deleted from the document.

Table content
-------------

The elements here are used to create and handle tabular data.

  Element                            Description
  ---------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<caption>`](element/caption)     Specifies the caption (or title) of a table.
  [`<col>`](element/col)             Defines a column within a table and is used for defining common semantics on all common cells. It is generally found within a [`<colgroup>`](element/colgroup) element.
  [`<colgroup>`](element/colgroup)   Defines a group of columns within a table.
  [`<table>`](element/table)         Represents tabular data --- that is, information presented in a two-dimensional table comprised of rows and columns of cells containing data.
  [`<tbody>`](element/tbody)         Encapsulates a set of table rows ([`<tr>`](element/tr) elements), indicating that they comprise the body of the table ([`<table>`](element/table)).
  [`<td>`](element/td)               Defines a cell of a table that contains data. It participates in the *table model*.
  [`<tfoot>`](element/tfoot)         Defines a set of rows summarizing the columns of the table.
  [`<th>`](element/th)               Defines a cell as a header of a group of table cells. The exact nature of this group is defined by the `scope` and `headers` attributes.
  [`<thead>`](element/thead)         Defines a set of rows defining the head of the columns of the table.
  [`<tr>`](element/tr)               Defines a row of cells in a table. The row\'s cells can then be established using a mix of [`<td>`](element/td) (data cell) and [`<th>`](element/th) (header cell) elements.

Forms
-----

HTML provides several elements that can be used together to create forms
that the user can fill out and submit to the website or application.
Further information about this available in the [HTML forms
guide](https://developer.mozilla.org/en-US/docs/Learn/Forms).

  Element                            Description
  ---------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<button>`](element/button)       An interactive element activated by a user with a mouse, keyboard, finger, voice command, or other assistive technology. Once activated, it performs an action, such as submitting a [form](https://developer.mozilla.org/en-US/docs/Learn/Forms) or opening a dialog.
  [`<datalist>`](element/datalist)   Contains a set of [`<option>`](element/option) elements that represent the permissible or recommended options available to choose from within other controls.
  [`<fieldset>`](element/fieldset)   Used to group several controls as well as labels ([`<label>`](element/label)) within a web form.
  [`<form>`](element/form)           Represents a document section containing interactive controls for submitting information.
  [`<input>`](element/input)         Used to create interactive controls for web-based forms to accept data from the user; a wide variety of types of input data and control widgets are available, depending on the device and user agent. The `<input>` element is one of the most powerful and complex in all of HTML due to the sheer number of combinations of input types and attributes.
  [`<label>`](element/label)         Represents a caption for an item in a user interface.
  [`<legend>`](element/legend)       Represents a caption for the content of its parent [`<fieldset>`](element/fieldset).
  [`<meter>`](element/meter)         Represents either a scalar value within a known range or a fractional value.
  [`<optgroup>`](element/optgroup)   Creates a grouping of options within a [`<select>`](element/select) element.
  [`<option>`](element/option)       Used to define an item contained in a select, an [`<optgroup>`](element/optgroup), or a [`<datalist>`](element/datalist) element. As such, `<option>` can represent menu items in popups and other lists of items in an HTML document.
  [`<output>`](element/output)       Container element into which a site or app can inject the results of a calculation or the outcome of a user action.
  [`<progress>`](element/progress)   Displays an indicator showing the completion progress of a task, typically displayed as a progress bar.
  [`<select>`](element/select)       Represents a control that provides a menu of options.
  [`<textarea>`](element/textarea)   Represents a multi-line plain-text editing control, useful when you want to allow users to enter a sizeable amount of free-form text, for example, a comment on a review or feedback form.

Interactive elements
--------------------

HTML offers a selection of elements that help to create interactive user
interface objects.

  Element                          Description
  -------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<details>`](element/details)   Creates a disclosure widget in which information is visible only when the widget is toggled into an \"open\" state. A summary or label must be provided using the [`<summary>`](element/summary) element.
  [`<dialog>`](element/dialog)     Represents a dialog box or other interactive component, such as a dismissible alert, inspector, or subwindow.
  [`<summary>`](element/summary)   Specifies a summary, caption, or legend for a details element\'s disclosure box. Clicking the `<summary>` element toggles the state of the parent [`<details>`](element/details) element open and closed.

Web Components
--------------

Web Components is an HTML-related technology that makes it possible to,
essentially, create and use custom elements as if it were regular HTML.
In addition, you can create custom versions of standard HTML elements.

  Element                            Description
  ---------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<slot>`](element/slot)           Part of the [Web Components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components) technology suite, this element is a placeholder inside a web component that you can fill with your own markup, which lets you create separate DOM trees and present them together.
  [`<template>`](element/template)   A mechanism for holding HTML that is not to be rendered immediately when a page is loaded but may be instantiated subsequently during runtime using JavaScript.

Obsolete and deprecated elements
--------------------------------

**Warning:** These are old HTML elements that are deprecated and should
not be used. **You should never use them in new projects, and you should
replace them in old projects as soon as you can.** They are listed here
for completeness only.

  Element                              Description
  ------------------------------------ ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [`<acronym>`](element/acronym)       Allows authors to clearly indicate a sequence of characters that compose an acronym or abbreviation for a word.
  [`<big>`](element/big)               Renders the enclosed text at a font size one level larger than the surrounding text (`medium` becomes `large`, for example). The size is capped at the browser\'s maximum permitted font size.
  [`<center>`](element/center)         Displays its block-level or inline contents centered horizontally within its containing element.
  `<content>`                          An obsolete part of the [Web Components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components) suite of technologies---was used inside of [Shadow DOM](https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_shadow_DOM) as an insertion point, and wasn\'t meant to be used in ordinary HTML. It has now been replaced by the [`<slot>`](element/slot) element, which creates a point in the DOM at which a shadow DOM can be inserted. Consider using [`<slot>`](element/slot) instead.
  [`<dir>`](element/dir)               Container for a directory of files and/or folders, potentially with styles and icons applied by the user agent. Do not use this obsolete element; instead, you should use the [`<ul>`](element/ul) element for lists, including lists of files.
  [`<font>`](element/font)             Defines the font size, color and face for its content.
  [`<frame>`](element/frame)           Defines a particular area in which another HTML document can be displayed. A frame should be used within a [`<frameset>`](element/frameset).
  [`<frameset>`](element/frameset)     Used to contain [`<frame>`](element/frame) elements.
  [`<image>`](element/image)           An ancient and poorly supported precursor to the [`<img>`](element/img) element. It should not be used.
  [`<marquee>`](element/marquee)       Used to insert a scrolling area of text. You can control what happens when the text reaches the edges of its content area using its attributes.
  [`<menuitem>`](element/menuitem)     Represents a command that a user is able to invoke through a popup menu. This includes context menus, as well as menus that might be attached to a menu button.
  [`<nobr>`](element/nobr)             Prevents the text it contains from automatically wrapping across multiple lines, potentially resulting in the user having to scroll horizontally to see the entire width of the text.
  [`<noembed>`](element/noembed)       An obsolete, non-standard way to provide alternative, or \"fallback\", content for browsers that do not support the embed element or do not support the type of [embedded content](content_categories#embedded_content) an author wishes to use. This element was deprecated in HTML 4.01 and above in favor of placing fallback content between the opening and closing tags of an [`<object>`](element/object) element.
  [`<noframes>`](element/noframes)     Provides content to be presented in browsers that don\'t support (or have disabled support for) the [`<frame>`](element/frame) element. Although most commonly-used browsers support frames, there are exceptions, including certain special-use browsers including some mobile browsers, as well as text-mode browsers.
  [`<param>`](element/param)           Defines parameters for an [`<object>`](element/object) element.
  [`<plaintext>`](element/plaintext)   Renders everything following the start tag as raw text, ignoring any following HTML. There is no closing tag, since everything after it is considered raw text.
  [`<rb>`](element/rb)                 Used to delimit the base text component of a ruby annotation, i.e. the text that is being annotated. One `<rb>` element should wrap each separate atomic segment of the base text.
  [`<rtc>`](element/rtc)               Embraces semantic annotations of characters presented in a ruby of [`<rb>`](element/rb) elements used inside of [`<ruby>`](element/ruby) element. [`<rb>`](element/rb) elements can have both pronunciation ([`<rt>`](element/rt)) and semantic ([`<rtc>`](element/rtc)) annotations.
  `<shadow>`                           An obsolete part of the [Web Components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components) technology suite that was intended to be used as a shadow DOM insertion point. You might have used it if you have created multiple shadow roots under a shadow host. Consider using [`<slot>`](element/slot) instead.
  [`<strike>`](element/strike)         Places a strikethrough (horizontal line) over text.
  [`<tt>`](element/tt)                 Creates inline text which is presented using the user agent default monospace font face. This element was created for the purpose of rendering text as it would be displayed on a fixed-width display such as a teletype, text-only screen, or line printer.
  [`<xmp>`](element/xmp)               Renders text between the start and end tags without interpreting the HTML in between and using a monospaced font. The HTML2 specification recommended that it should be rendered wide enough to allow 80 characters per line.

See also
--------

- [`Element`](https://developer.mozilla.org/en-US/docs/Web/API/Element)
    interface

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/HTML/Element>>