# **HTML**

_Fundamentals, common tags and best practices_

<br>

## Overview

This study guide will hold a list of commonly use tags, along with best practices and examples.

<br>
<br>

---

## **Quick notes**

This section is a quick reference point for certain HTML guidelines that I'll need to review often, such as which semantic tags to use where, and other best practices to keep in mind. I'll also include a section for accessibility since this ties into many parts of html in the form of properties, e.g. `aria-required="true"`. These don't usually change your app but can assist screen readers and improve SEO.

<br>
<br>

#### **Empty elements**

Instead of leaving an element empty, you can leave a space in there. But a better practice would be to use an `html entity` such as `&nbsp;` _(`N`on `B`reaking `Sp`ace)_.

```html
<button class="dot">&nbsp;</button>
```

<br>
<br>

#### **Void elements**

A void element is an element in HTML that cannot have any child nodes. Void elements only have a start tag, no end tags. We refer to this as a **self-closing tag**.

```html
<img src="source/example.png" />
```

HTML doesn't actually require a slash to close the tag, even pre HTML 5. So this syntax is cleaner.

```html
<img src="source/example.png" />
<!-- No slash-->
```

<br>

Here are some examples of void elements:

-   \<area>

-   \<base>
-   \<br>
-   \<col>
-   \<hr>
-   \<img>
-   \<input>
-   \<link>
-   \<meta>
-   \<param>
-   \<source>
-   \<track>

<br>
<br>

#### **Creating a card**

When creating a card, it's very common to use a `<figure>` tag to wrap the contents. Also acceptable could be an `<article>` tag.

<br>
<br>

#### **Images**

Use the `<picture>` tag to specify which image (_`<img>`_) should be loaded, depending on the screen size. This will not load all images and then hide some, this also isn't the same as creating a media query (although similar), this simply only displays the specified source (_`<src>`_) depending on the user's screen size.

<br>

Example:

```html
<picture>
    <source media="(min-width: 650px)" srcset="img_food.jpg" />

    <source media="(min-width: 465px)" srcset="img_car.jpg" />

    <img src="img_girl.jpg" />
</picture>
```

<br>
<br>

#### **Nav vs Menu**

The `<nav>` and `<menu>` tag might seem the same, but there's actually a key difference. `<nav>` is far more common, and used on most site for navigation. It contains a bunch of links that typically lead to other places in the website or web application. **Menu** however, is far less common and is used for menu buttons in an actual web application _(such as outlook)_.

<br>

_Navigation links_

![Gmail navigation](img/html/email_navigation.png)

<br>

_Menu buttons_

![Gmail buttons](img/html/menu_buttons.png)

<br>
<br>

#### **\<body> misconception**

The `<body>` does not magically take up the entire height of the screen. It behaves like any other element, which will only take the space it needs.

<br>
<br>

---

## **HTML Elements Reference**

<br>
<br>

## Main root

<br>

#### `<html>`

The _\<html>_ HTML element represents the root (top-level element) of an HTML document, so it is also referred to as the root element. All other elements must be descendants of this element.

<br>
<br>

## Document metadata

Metadata contains information about the page. This includes information about styles, scripts and data to help software (search engines, browsers, etc.) use and render the page. Metadata for styles and scripts may be defined in the page or link to another file that has the information.

<br>

#### `<head>`

The _\<head>_ HTML element contains machine-readable information (metadata) about the document, like its title, scripts, and style sheets.

<br>

#### `<link>`

The _\<link>_ HTML element specifies relationships between the current document and an external resource. This element is most commonly used to link to CSS, but is also used to establish site icons (both "favicon" style icons and icons for the home screen and apps on mobile devices) among other things.

<br>

#### `<meta>`

The _\<meta>_ HTML element represents Metadata that cannot be represented by other HTML meta-related elements, like base, link, script, style or title.

<br>

#### `<style>`

The _\<style\>_ HTML element contains style information for a document, or part of a document. It contains CSS, which is applied to the contents of the document containing the \<style\> element.

<br>

#### `<title>`

The _\<title>_ HTML element defines the document's title that is shown in a Browser's title bar or a page's tab. It only contains text; tags within the element are ignored.

<br>
<br>

## Sectioning root

#### `<body>`

The _\<body>_ HTML element represents the content of an HTML document. There can be only one \<body> element in a document.

<br>
<br>

## Content sectioning

Content sectioning elements allow you to organize the document content into logical pieces. Use the sectioning elements to create a broad outline for your page content, including header and footer navigation, and heading elements to identify sections of content.

<br>

#### `<address>`

The _\<address>_ HTML element indicates that the enclosed HTML provides contact information for a person or people, or for an organization.

![HTML address tag example](img/html/address_example.png)

<br>

#### `<article>`

The _\<article>_ HTML element represents a self-contained composition in a document, page, application, or site, which is intended to be independently distributable or reusable (e.g., in syndication). Examples include: a forum post, a magazine or newspaper article, or a blog entry, a product card, a user-submitted comment, an interactive widget or gadget, or any other independent item of content.

> "The \<article> element is used to represent something that could be plucked out of your page and dropped into another and still make sense on its own. This might be a literal article or blog post, but could also be used for a social media post like a tweet or a Facebook wall post."

<br>

#### `<aside>`

The _\<aside>_ HTML element represents a portion of a document whose content is only indirectly related to the document's main content. Asides are frequently presented as sidebars or call-out boxes.

<br>

#### `<footer>`

The _\<footer>_ HTML element represents a footer for its nearest ancestor sectioning content or sectioning root element. A _\<footer>_ typically contains information about the author of the section, copyright data or links to related documents. You should use the _\<address>_ tag to store author info. Also worth noting, there can be multiple footer tags in a file, as it usually denotes the end of a section; however, you cannot use a _\<footer>_ tag inside of another _\<footer>_.

<br>

#### `<header>`

The _\<header>_ HTML element represents introductory content, typically a group of introductory or navigational aids. It may contain some heading elements but also a logo, a search form, an author name, and other elements. The _\<header>_ tag is usually used at the top of a section and holds the heading (_\<h1-6>_) inside of it. You can have more than one _\<header>_ tag in a file, but you can't nest a _\<header>_ in a _\<header>_.

<br>

#### `<h1>, <h2>, <h3>, <h4>, <h5>, <h6>,`

The _\<h1>_ to _\<h6>_ HTML element represent six levels of section headings. \<h1> is the highest section level and \<h6> is the lowest.

<br>

#### `<main>`

The _\<main>_ HTML element represents the dominant content of the body of a document. The main content area consists of content that is directly related to or expands upon the central topic of a document, or the central functionality of an application. There must not be more than one visible \<main> element in a document. If more than one \<main> element is present in a document, all other instances must be hidden using the `hidden` attribute.

> "So \<main> is where you put the good stuff, the important parts of a page, the reason the user came to this page in particular, not your site in general. In other words, the main content.😯😲🤯
>
> All that other stuff, logos and search forms and navigation and such, can go in a \<header> or \<footer> within the \<body> but outside of \<main>."

<br>

#### `<nav>`

The _\<nav>_ HTML element represents a section of a page whose purpose is to provide navigation links, either within the current document or to other documents. Common examples of navigation sections are menus, tables of contents, and indexes.

<br>

#### `<section>`

The _\<section>_ HTML element represents a generic standalone section of a document, which doesn't have a more specific semantic element to represent it. Sections should always have a heading, with very few exceptions.

> "Structurally speaking, it's basically just a <div> with special semantic meaning. A _\<section>_ begins a new "sectioning content" region, so it can have its own \<header> and/or \<footer>."

<br>
<br>

## Text content

Use HTML text content elements to organize blocks or sections of content placed between the opening \<body> and closing \</body> tags. Important for accessibility and SEO, these elements identify the purpose or structure of that content.

<br>

#### `<blockquote>`

The _\<blockquote>_ HTML element indicates that the enclosed text is an extended quotation. Usually, this is rendered visually by indentation (see Notes for how to change it). A URL for the source of the quotation may be given using the cite attribute, while a text representation of the source can be given using the cite element.

<br>

#### `<div>`

The _\<div>_ HTML element is the generic container for flow content. It has no effect on the content or layout until styled in some way using CSS (e.g. styling is directly applied to it, or some kind of layout model like Flexbox is applied to its parent element).

<br>

#### `<figcaption>`

The _\<figcaption>_ HTML element represents a caption or legend describing the rest of the contents of its parent figure element.

<br>

#### `<figure>`

The _\<figure>_ HTML element represents self-contained content, potentially with an optional caption, which is specified using the figcaption element. The figure, its caption, and its contents are referenced as a single unit.

<br>

#### `<hr>`

The _\<hr>_ HTML element represents a thematic break between paragraph-level elements: for example, a change of scene in a story, or a shift of topic within a section.

<br>

#### `<menu>`

The _\<menu>_ HTML element is described in the HTML specification as a semantic alternative to ul, but treated by browsers (and exposed through the accessibility tree) as no different than ul. It represents an unordered list of items (which are represented by li elements).

<br>

#### `<ol>`

The _\<ol>_ HTML element represents an ordered list of items — typically rendered as a numbered list.

<br>

#### `<ul>`

The _\<ul>_ HTML element represents an unordered list of items, typically rendered as a bulleted list.

<br>

#### `<li>`

The _\<li>_ HTML element is used to represent an item in a list. It must be contained in a parent element: an ordered list (ol), an unordered list (ul), or a menu (menu). In menus and unordered lists, list items are usually displayed using bullet points. In ordered lists, they are usually displayed with an ascending counter on the left, such as a number or letter.

<br>

#### `<p>`

The _\<p>_ HTML element is used to represent an item in a list. It must be contained in a parent element: an ordered list (ol), an unordered list (ul), or a menu (menu). In menus and unordered lists, list items are usually displayed using bullet points. In ordered lists, they are usually displayed with an ascending counter on the left, such as a number or letter.

<br>

#### `<pre>`

The _\<pre>_ HTML element represents preformatted text which is to be presented exactly as written in the HTML file. The text is typically rendered using a non-proportional, or monospaced, font. Whitespace inside this element is displayed as written.

<br>
<br>

## Inline text semantics

Use the HTML inline text semantic to define the meaning, structure, or style of a word, line, or any arbitrary piece of text.

<br>

#### `<a>`

The _\<a>_ HTML element (or anchor element), with its `href` attribute, creates a hyperlink to web pages, files, email addresses, locations in the same page, or anything else a URL can address.

> "The a element may be wrapped around entire paragraphs, lists, tables, and so forth, even entire sections, so long as there is no interactive content within (e.g. buttons or other links)."

<br>

In other words, you can nest any elements inside an `<a>` tag except the following:

```html
<a>
<audio> <!--(if the controls attribute is present)-->
<button>
<details>
<embed>
<iframe>
<img> <!--(if the usemap attribute is present)-->
<input> <!--(if the type attribute is not in the hidden state)-->
<label>
<menu> <!--(if the type attribute is in the toolbar state)-->
<object> <!--(if the usemap attribute is present)-->
<select>
<textarea>
<video> <!--(if the controls attribute is present)-->
```

<br>
<br>

#### `<br>`

The _\<br>_ HTML element produces a line break in text (carriage-return). It is useful for writing a poem or an address, where the division of lines is significant.

<br>

#### `<cite>`

The _\<cite>_ HTML element element is used to describe a reference to a cited creative work, and must include the title of that work. The reference may be in an abbreviated form according to context-appropriate conventions related to citation metadata.

<br>

#### `<code>`

The _\<code>_ HTML element displays its contents styled in a fashion intended to indicate that the text is a short fragment of computer code. By default, the content text is displayed using the user agent default monospace font.

<br>

#### `<em>`

The _\<em>_ HTML element marks text that has stress emphasis. The \<em> element can be nested, with each level of nesting indicating a greater degree of emphasis.

<br>

#### `<i>`

The _\<i>_ HTML element represents a range of text that is set off from the normal text for some reason, such as idiomatic text, technical terms, taxonomical designations, among others. Historically, these have been presented using italicized type, which is the original source of the \<i> naming of this element.

<br>

#### `<mark>`

The _\<mark>_ HTML element represents text which is marked or highlighted for reference or notation purposes, due to the marked passage's relevance or importance in the enclosing context.

<br>

#### `<small>`

The _\<small>_ HTML element represents side-comments and small print, like copyright and legal text, independent of its styled presentation. By default, it renders text within it one font-size smaller, such as from small to x-small.

<br>

#### `<span>`

The _\<span>_ HTML element is a generic inline container for phrasing content, which does not inherently represent anything. It can be used to group elements for styling purposes (using the class or id attributes), or because they share attribute values, such as lang. It should be used only when no other semantic element is appropriate. \<span> is very much like a div element, but div is a block-level element whereas a \<span> is an inline element.

<br>

#### `<strong>`

The _\<strong>_ HTML element indicates that its contents have strong importance, seriousness, or urgency. Browsers typically render the contents in bold type.

<br>

#### `<q>`

The _\<q>_ HTML element indicates that the enclosed text is a short inline quotation. Most modern browsers implement this by surrounding the text in quotation marks. This element is intended for short quotations that don't require paragraph breaks; for long quotations use the blockquote element.

<br>
<br>

## Image and multimedia

HTML supports various multimedia resources such as images, audio, and video.

<br>

#### `<audio>`

The _\<audio>_ HTML element is used to embed sound content in documents. It may contain one or more audio sources, represented using the src attribute or the source element: the browser will choose the most suitable one. It can also be the destination for streamed media, using a MediaStream.

<br>

#### `<img>`

The _\<img>_ HTML element embeds an image into the document.

<br>

#### `<video>`

The _\<video>_ HTML element element embeds a media player which supports video playback into the document. You can use \<video> for audio content as well, but the audio element may provide a more appropriate user experience.

<br>

#### `<track>`

The _\<track>_ HTML element is used as a child of the media elements, audio and video. It lets you specify timed text tracks (or time-based data), for example to automatically handle subtitles. The tracks are formatted in WebVTT format (.vtt files) — Web Video Text Tracks.

<br>
<br>

## Embedded content

In addition to regular multimedia content, HTML can include a variety of other content, even if it's not always easy to interact with.

<br>

#### `<embed>`

The _\<embed>_ HTML element embeds external content at the specified point in the document. This content is provided by an external application or other source of interactive content such as a browser plug-in.

<br>

#### `<picture>`

The _\<picture>_ HTML element contains zero or more source elements and one img element to offer alternative versions of an image for different display/device scenarios.

<br>

#### `<source>`

The _\<source>_ HTML element specifies multiple media resources for the picture, the audio element, or the video element. It is an empty element, meaning that it has no content and does not have a closing tag. It is commonly used to offer the same media content in multiple file formats in order to provide compatibility with a broad range of browsers given their differing support for image file formats and media file formats.

<br>
<br>

## SVG

You can embed SVG content directly into HTML documents, using the _\<svg>_ element.

<br>

#### `<svg>`

The \<svg> element is a container that defines a new coordinate system and viewport. It is used as the outermost element of SVG documents, but it can also be used to embed an SVG fragment inside an SVG or HTML document.

<br>
<br>

## Scripting

In order to create dynamic content and Web applications, HTML supports the use of scripting languages, most prominently JavaScript. Certain elements support this capability.

<br>

#### `<canvas>`

Use the HTML \<canvas> element with either the canvas scripting API or the WebGL API to draw graphics and animations.

<br>

#### `<noscript>`

The _\<noscript>_ HTML element defines a section of HTML to be inserted if a script type on the page is unsupported or if scripting is currently turned off in the browser.

<br>

#### `<script>`

The _< script>_ HTML element is used to embed executable code or data; this is typically used to embed or refer to JavaScript code. The < script> element can also be used with other languages, such as WebGL's GLSL shader programming language and JSON.

<br>
<br>

## Table content

The elements here are used to create and handle tabular data.

<br>

#### `<table>`

The _\<table>_ HTML element represents tabular data — that is, information presented in a two-dimensional table comprised of rows and columns of cells containing data.

<br>

#### `<thead>`

The _\<thead>_ HTML element defines a set of rows defining the head of the columns of the table.

<br>

#### `<tbody>`

tbodye _\<th>_ HTML element encapsulates a set of table rows (tr elements), indicating that they comprise the body of the table (table).

<br>

#### `<tfooter>`

The _\<tfooter>_ HTML element defines a set of rows summarizing the columns of the table.

<br>

#### `<th>`

The _\<th>_ HTML element defines a cell as header of a group of table cells. The exact nature of this group is defined by the scope and headers attributes.

<br>

#### `<tr>`

The _\<tr>_ HTML element defines a row of cells in a table. The row's cells can then be established using a mix of td (data cell) and th (header cell) elements.

<br>

#### `<td>`

The _\<td>_ HTML element defines a cell of a table that contains data. It participates in the table model.

<br>

#### `<col>`

The _\<col>_ HTML element defines a column within a table and is used for defining common semantics on all common cells. It is generally found within a colgroup element.

<br>

#### `<colgroup>`

The _\<colgroup>_ HTML element defines a group of columns within a table.

<br>

#### `<caption>`

The _\<caption>_ HTML element specifies the caption (or title) of a table.

<br>
<br>

#### **Removing table inner border**

The `border-collapse` CSS property sets whether cells inside a `<table>` have shared or separate borders.

<br>

```css
border-collapse: collapse;
```

![table with collapsed borders](img/css/collapsed_border.png)

<br>
<br>

```css
border-collapse: separate;
```

![table with separated borders](img/css/separated_border.png)

<br>
<br>

## Forms

HTML provides a number of elements which can be used together to create forms which the user can fill out and submit to the Web site or application. There's a great deal of further information about this available in the HTML forms guide.

<br>

#### `<form>`

The \<form> HTML element represents a document section containing interactive controls for submitting information.

<br>

#### `<label>`

The \<label> HTML element represents a caption for an item in a user interface.

<br>

#### `<input>`

The \<input> HTML element is used to create interactive controls for web-based forms in order to accept data from the user; a wide variety of types of input data and control widgets are available, depending on the device and user agent. The \<input> element is one of the most powerful and complex in all of HTML due to the sheer number of combinations of input types and attributes.

<br>

#### `<output>`

The \<output> HTML element is a container element into which a site or app can inject the results of a calculation or the outcome of a user action.

<br>

#### `<textarea>`

The \<textarea> HTML element represents a multi-line plain-text editing control, useful when you want to allow users to enter a sizeable amount of free-form text, for example a comment on a review or feedback form.

<br>

#### `<button>`

The <button>button</button> HTML element is an interactive element activated by a user with a mouse, keyboard, finger, voice command, or other assistive technology. Once activated, it then performs a programmable action, such as submitting a form or opening a dialog.

<br>

#### `<select>`

The \<select> HTML element represents a control that provides a menu of options.

<br>

#### `<option>`

The \<option> HTML element is used to define an item contained in a select, an optgroup, or a datalist element. As such, \<option> can represent menu items in popups and other lists of items in an HTML document.

<br>

#### `<optgroup>`

The \<optgroup> HTML element

<br>

#### `<datalist>`

The \<datalist> HTML element contains a set of option elements that represent the permissible or recommended options available to choose from within other controls.

<br>

#### `<fieldset>`

The \<fieldset> HTML element is used to group several controls as well as labels (label) within a web form.

<br>

#### `<legend>`

The \<legend> HTML element represents a caption for the content of its parent fieldset.

<br>

#### `<meter>`

The \<meter> HTML element represents either a scalar value within a known range or a fractional value.

<br>

#### `<progress>`

The \<progress> HTML element displays an indicator showing the completion progress of a task, typically displayed as a progress bar.

<br>
<br>

---

## **HTML entities**

<br>

An HTML entity is a piece of text (`"string"`) that begins with an ampersand _(`&`)_ and ends with a semicolon _(`;`)_. Entities are frequently used to display reserved characters _(which would otherwise be interpreted as HTML code)_, and invisible characters _(like non-breaking spaces)_. You can also use them in place of other characters that are difficult to type with a standard keyboard.

<br>

![HTML entities chart](img/html/html_entities.png)

<br>

> <span style="color: #007ACC;">Note</span>: Many characters have memorable entities. For example, the entity for the copyright symbol (`©`) is `&copy;`. For less memorable characters, such as `&#8212;` or `&#x2014;`, you can use a [reference chart](https://html.spec.whatwg.org/multipage/named-characters.html#named-character-references)

<br>
<br>

---

## **Emmet plugin**

Emmet uses syntax similar to CSS selectors for describing elements’ positions inside generated tree and elements’ attributes. You can use elements’ names like `div` or `p` to generate HTML tags.

Emmet doesn’t have a predefined set of available tag names, you can write any word and transform it into a tag: div → `<div></div>`, foo → `<foo></foo>` and so on.

![Emmet cheat sheet](img/html/emmet_cheat-sheet.png)

[Full Emmet cheat sheet](https://docs.emmet.io/cheat-sheet/)

<br>
<br>

### Nesting operators

Nesting operators are used to position abbreviation elements inside generated tree: whether it should be placed inside or near the context element.

<br>
<br>

#### **`Child: >`**

You can use the `>` operator to nest elements inside each other:

```emmet
div>ul>li
```

<br>
Will produce...

```html
<div>
    <ul>
        <li></li>
    </ul>
</div>
```

<br>
<br>

#### **`Sibling: +`**

Use the `+` operator to place elements near each other, on the same level:

```emmet
div+p+bq
```

<br>

...will output

```html
<div></div>
<p></p>
<blockquote></blockquote>
```

<br>
<br>

#### **`Climb-up: ^`**

With the `^` operator, you can climb one level up the tree and change context where following elements should appear:

```
div+div>p>span+em^bq
```

<br>

...outputs

```html
<div></div>
<div>
    <p><span></span><em></em></p>
    <blockquote></blockquote>
</div>
```

<br>

You can use as many `^` operators as you like, each operator will move one level up:

```
div+div>p>span+em^^^bq
```

<br>

will output

```html
<div></div>
<div>
    <p><span></span><em></em></p>
</div>
<blockquote></blockquote>
```

<br>
<br>

#### **`Multiplication: *`**

With the `*` operator you can define how many times element should be outputted:

```emmet
ul>li\*5
```

<br>

...outputs

```html
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

<br>
<br>

#### **`Grouping: ()`**

Parenthesises are used for grouping subtrees in complex abbreviations:

<br>

```emmet
div>(header>ul>li\*2>a)+footer>p
```

<br>

...expands to

```html
<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

<br>

You can nest groups inside each other and combine them with the multiplication `*` operator:

```emmet
(div>dl>(dt+dd)\*3)+footer>p
```

<br>

...produces

```html
<div>
    <dl>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
    </dl>
</div>
<footer>
    <p></p>
</footer>
```

With groups, you can literally write full page mark-ups with a single abbreviation, but please don’t do that 😅.

<br>
<br>

#### **`Attribute operators`**

Attribute operators are used to modify attributes of outputted elements. For example, in HTML and XML you can quickly add class attributes to generated elements.

<br>

##### **ID and CLASS**

In CSS, you use elem`#id` and elem`.class` notation to reach the elements with specified id or class attributes. In Emmet, you can use the very same syntax to add these attributes to specified element:

```
div#header+div.page+div#footer.class1.class2.class3
```

<br>

...will output

```html
<div id="header"></div>
<div class="page"></div>
<div id="footer" class="class1 class2 class3"></div>
```

<br>
<br>

##### **Custom attributes**

You can use `[attr]` notation (as in CSS) to add custom attributes to your element:

```emmet
td[title="Hello world!" colspan=3]
```

<br>

...outputs

```html
<td title="Hello world!" colspan="3"></td>
```

<br>

You can place as many attributes as you like inside square brackets.
You don’t have to specify attribute values: `td[colspan title]` will produce

```html
<td colspan="" title=""></td>
```

<br>

You can use single or double quotes for quoting attribute values.
You don’t need to quote values if they don’t contain spaces: `td[title=hello colspan=3]` will work.

<br>
<br>

#### **`Item numbering: $`**

With the multiplication `*` operator you can repeat elements, but with `$` you can number them. Place the `$` operator inside element’s name, attribute’s name or attribute’s value to output current number of repeated element:

```emmet
ul>li.item$\*5
```

<br>

...outputs to

```html
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
</ul>
```

<br>

You can use multiple `$` in a row to pad number with zeroes:

```emmet
ul>li.item$$$\*5
```

<br>

...outputs to

```html
<ul>
    <li class="item001"></li>
    <li class="item002"></li>
    <li class="item003"></li>
    <li class="item004"></li>
    <li class="item005"></li>
</ul>
```

<br>
<br>

#### **`Changing numbering base and direction`**

With the `@` modifier, you can change numbering direction (ascending or descending) and base (e.g. start value).

<br>

For example, to change direction, add `@-` after `$`:

```emmet
ul>li.item$@-\*5
```

<br>

…outputs to

```html
<ul>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
    <li class="item2"></li>
    <li class="item1"></li>
</ul>
```

<br>

To change the counter base value, add `@N` modifier to `$`:

```emmet
ul>li.item$@3\*5
```

<br>

…transforms to

```html
<ul>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
    <li class="item6"></li>
    <li class="item7"></li>
</ul>
```

<br>

You can use these modifiers together:

```
ul>li.item$@-3\*5
```

<br>

…is transformed to

```html
<ul>
    <li class="item7"></li>
    <li class="item6"></li>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
</ul>
```

<br>
<br>

#### **`Text: {}`**

You can use curly braces to add text to element:

```emmet
a{Click me}
```

<br>

...will produce

```html
<a href="">Click me</a>
```

<br>
<br>

Note that `{text}` is used and parsed as a separate element (like, `div`, `p` etc.) but has a special meaning when written right after element. For example, `a{click}` and `a>{click}` will produce the same output, but `a{click}+b{here}` and `a>{click}+b{here}` won’t:

<br>

```html
<!-- a{click}+b{here} -->

<a href="">click</a><b>here</b>
```

<br>

```html
<!-- a>{click}+b{here} -->

<a href="">click<b>here</b></a>
```

In the second example, the `<b>` element is placed inside `<a>` element, and that’s the difference. When `{text}` is written right after an element, it doesn’t change its parent context.

<br>
<br>

#### **`Notes on abbreviation formatting`**

When you get familiar with Emmet’s abbreviations syntax, you may want to use some formatting to make your abbreviations more readable. For example, use spaces between elements and operators.

<br>

Like this:

```emmet
(header > ul.nav > li\*5) + footer
```

<br>

<mark>But it won’t work, because space is a stop symbol where Emmet stops abbreviation parsing.</mark> Many users mistakenly think that each abbreviation should be written in a new line, but they are **wrong**; you can type and expand abbreviation anywhere in the text:

[More complete guide here](https://docs.emmet.io/abbreviations/syntax/)

<br>
<br>

## **ARIA - Accessibility**

> Accessible Rich Internet Applications ( ARIA ) is a set of roles and attributes that define ways to make web content and web applications (especially those developed with JavaScript) more accessible to people with disabilities.
_[MDN (Mozilla Developer Network)](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)_

ARIA (_Accessible Rich Internet Applications_) is an important part of modern web development and ensures that people with certain disabilities can still access your site. Depending on the type of website you are building, this could be one of your main priorities. For instance, if you have a commerce site, the more people who can access it, the better. But if you have a specific app for a person who doesn't care about accessibility, then you might focus on neat features instead. Although always optional, it's a good habit to include ARIA markup in your html to help AT (_assistive technologies_).

<br>

#### **Role Property**

The role property tells assistive technologies what that element's purpose is. Although there is no official  HTML5 specification that standardizes a list of valid role values, it's best practice to use the commonly used words since those have a higher chance of being interpreted correctly. Giving a role property a custom value like "button-for-last-about-me" might not be the best choice. It's also important not to confuse role with the `id=""` property, although they can be named similarly at times.

**List of commonly used role values**

- **alert:** Used for important, usually time-sensitive, information.

- **alertdialog:** Used for modal alert dialogs that interrupt a user’s workflow to communicate an important message and require a response.
- **application:** Indicates that an element and all of its children should be treated similar to a desktop application.
- **article:** Indicates a section of a page that could easily stand on its own on a page, in a document, or on a website.
- **banner:** Defines a global site header, which usually includes a logo, company name, search feature, and possibly the global navigation or a slogan.
- **button:** Used for clickable elements that trigger a response when activated by the user.
- **cell:** Denotes the element’s contents as data in a table cell.
- **checkbox:** Used for checkable interactive controls.
- **columnheader:** Identifies an element as being a cell in a row that contains header information for a column.
- **combobox:** Identifies an element as an input that controls another element, such as a listbox or grid, that can dynamically pop up to help the user set the value of that input.
- **complementary:** Represents a supporting section of the document, designed to be complementary to the main content at a similar level in the DOM hierarchy[^search_web(query=“HTML role complementary”)].
- **contentinfo:** Represents a large perceivable region that contains information about the parent document[^search_web(query=“HTML role contentinfo”)].
- **definition:** Indicates the term being defined within a definition list[^search_web(query=“HTML role definition”)].
- **dialog:** Represents a dialog or other interactive application window[^search_web(query=“HTML role dialog”)].
- **directory:** Represents a list of references to members of a group, such as a static table of contents[^search_web(query=“HTML role directory”)].
- **document:** Represents a standalone document that is embedded in a parent document[^search_web(query=“HTML role document”)].
- **feed:** Represents a scrollable list of articles where scrolling may cause articles to be added to or removed from either end of the list[^search_web(query=“HTML role feed”)].
- **figure:** Represents a unit of content, optionally with a caption, that is self-contained, that is typically referenced as a single unit from the main flow of the document[^search_web(query=“HTML role figure”)].
- **form:** Represents a section of a page that consists of a form, including form controls and labels[^search_web(query=“HTML role form”)].
- **grid:** Represents a control that presents a collection of hierarchical or tabular data across two dimensions[^search_web(query=“HTML role grid”)].
- **gridcell:** Represents a cell in a grid or treegrid[^search_web(query=“HTML role gridcell”)].
- **group:** Represents a set of user interface objects which are not intended to be included in a page summary or table of contents by assistive technologies[^search_web(query=“HTML role group”)].
- **heading:** Represents a heading for a section of the page[^search_web(query=“HTML role heading”)].
- **img:** Represents a container for a collection of elements that form an image[^search_web(query=“HTML role img”)].
- **link:** Represents an interactive reference to a resource[^search_web(query=“HTML role link”)].
- **list:** Represents a list of items[^search_web(query=“HTML role list”)].
- **listbox:** Represents a widget that allows the user to select one or more items from a list of choices[^search_web(query=“HTML role listbox”)].
- **listitem:** Represents a single item in a list or directory[^search_web(query=“HTML role listitem”)].
- **log:** Represents a type of live region where new information is added in meaningful order and old information may disappear[^search_web(query=“HTML role log”)].
- **main:** Represents the main content of a document[^search_web(query=“HTML role main”)].
- **marquee:** Represents a section of a page where the content is displayed in a manner that is similar to a mechanical billboard[^search_web(query=“HTML role marquee”)].
- **math:** Represents a block of mathematical content[^search_web(query=“HTML role math”)].
- **menu:** Represents a type of widget that offers a list of choices to the user[^search_web(query=“HTML role menu”)].
- **menubar:** Represents a presentation of menu that usually remains visible and is usually presented horizontally[^search_web(query=“HTML role menubar”)].
- **menuitem:** Represents an option in a set of choices contained by a menu or menubar[^search_web(query=“HTML role menuitem”)].
- **menuitemcheckbox:** Represents a checkable menuitem within a menu[^search_web(query=“HTML role menuitemcheckbox”)].
- **menuitemradio:** Represents a checkable menuitem in a group of menuitemradio roles, only one of which can be checked at a time[^search_web(query=“HTML role menuitemradio”)].
- **navigation:** Represents a section of a page that contains navigation links[^search_web(query=“HTML role navigation”)].
- **none:** Represents an element that is not visible, perceivable, or interactive to any user[^search_web(query=“HTML role none”)].
- **note:** Represents a section of a page that consists of a note that is separate from the main content[^search_web(query=“HTML role note”)].
- **option:** Represents an option in a listbox[^search_web(query=“HTML role option”)].
- **presentation:** An element is used to change the look of its parent or other elements without changing their meaning or functionality[^search_web(query=“HTML role presentation”)].
- **progressbar:** Represents a range of user input or application progress[^search_web(query=“HTML role progressbar”)].
- **radio:** Represents a checkable input in a group, where only one in the group can be checked[^search_web(query=“HTML role radio”)].
- **radiogroup:** Represents a group of radio buttons[^search_web(query=“HTML role radiogroup”)].
- **region:** Represents a large perceivable section of a web page or document[^search_web(query=“HTML role region”)].
- **row:** Represents a row of cells in a grid[^search_web(query=“HTML role row”)].
- **rowgroup:** Represents a group of one or more rows in a grid[^search_web(query=“HTML role rowgroup”)].
- **rowheader:** Identifies an element as a cell in a row that contains header information for that row[^search_web(query=“HTML role rowheader”)].
- **scrollbar:** Represents a scrollbar[^search_web(query=“HTML role scrollbar”)].
- **search:** Represents a landmark region that contains a collection of items and objects that, as a whole, combine to create a search facility[^search_web(query=“HTML role search”)].
- **searchbox:** Represents a text input that a user can enter search queries into[^search_web(query=“HTML role searchbox”)].
- **separator:** Represents a line or bar that separates and distinguishes sections of content or groups of menuitems[^search_web(query=“HTML role separator”)].
- **slider:** Represents an input that allows the user to select a value within a given range[^search_web(query=“HTML role slider”)].
- **spinbutton:** Represents an input that allows the user to choose a value from within a given range[^search_web(query=“HTML role spinbutton”)].
- **status:** Represents a container whose content is advisory information for the user that is not important enough to justify an alert[^search_web(query=“HTML role status”)].
- **switch:** Represents a checkbox that can be turned on and off[^search_web(query=“HTML role switch”)].
- **tab:** Represents a header for a tabpanel[^search_web(query=“HTML role tab”)].
- **table:** Represents tabular data[^search_web(query=“HTML role table”)].
- **tablist:** Represents a list of tabs, which are references to tabpanels[^search_web(query=“HTML role tablist”)].
- **tabpanel:** Represents a container for the resources associated with a tab[^search_web(query=“HTML role tabpanel”)].
- **term:** Represents a term or phrase with a corresponding definition[^search_web(query=“HTML role term”)].
- **textbox:** Represents a text input that allows free-form text as its value[^search_web(query=“HTML role textbox”)].
- **timer:** Represents a numeric counter that indicates an amount of elapsed time from a start point, or the time remaining until an end point[^search_web(query=“HTML role timer”)].
- **toolbar:** Represents a collection of commonly used function represented in compact visual form[^search_web(query=“HTML role toolbar”)].
- **tooltip:** Represents a popup that displays a description for an element when it receives keyboard focus or the mouse hovers over it[^search_web(query=“HTML role tooltip”)].
- **tree:** Represents a tree structure that contains items that may be expanded and collapsed[^search_web(query=“HTML role tree”)].
- **treegrid:** Represents a grid that contains cells that may expand to reveal additional rows[^search_web(query=“HTML role treegrid”)].
- **treeitem:** Represents an option item of a tree. This is an element within a tree that may be expanded or collapsed if it contains a sub-level group of treeitem elements[^search_web(query=“HTML role treeitem”)].

<br>

Sometimes when specifying a role, you will also need to provide additional properties. For instance consider a `<div>`, div's have no semantic meaning and by default are non-interactive and not focusable, meaning users relying on a keyboard can't tab to them and assistive technologies might not be able to select them either. So if we give a `<div>` a `role="menu"`, that implies that the user can select things from that menu, but that won't be possible even if the AT(_assitive technologies_) know it's a menu. In cases like these you will need to provide additional info such as the `tabindex=""` property.

<br>
<br>

#### **Tabindex**

The tabindex attribute is used to make an element focusable and to control the position of the element in the navigation order. When you include `tabindex="0"` on an element with `role="menu"`, you’re making that element focusable and placing it in the natural tab order of the content. This allows keyboard users to tab to the menu and interact with it.

A tabindex with a negative value, specifically -1, means that the element is focusable, but it’s not reachable via sequential keyboard navigation. It’s only focusable programmatically (_i.e., through JavaScript_) or by clicking on it with the mouse. This is often used to take elements out of the natural tab order, but still allow them to receive focus. For example, you might do this for a modal dialog box that should receive focus when it’s visible, but not be in the tab order when it’s hidden.

```js
  <div role="menu" tabindex="-1">
    <div role="menuitem">Menu Item 1</div>
    <div role="menuitem">Menu Item 2</div>
  </div>
```

<br>
<br>

### **Accessible Forms**

Forms have semantic syntax specific to forms, elements such as `<label>` and properties such as `aria-required=""` are some examples.

<br>

#### **Aria-label & aria-required**

Imagine you have a searchbar with a placeholder, like a Google search. There's no label for that input, so people using screen readers might not be able to understand what that searchbar does. In this case you can use the `aria-label` property.

```html
    <!-- Not explicit, can't be interpreted by screen readers -->
    ❌<input placeholder="Type to search" />

    <!-- Explicit, can be interpreted by screen readers -->
    ✅<input placeholder="Type to search" aria-label="Type to search" />

    <!-- Explicit, can be interpreted by screen readers -->
    <label for="first-name">Please enter your first name. <span class="color-red">*</span></label>
    <input id="first-name" name="first-name" placeholder="first-name" required aria-required="true">
```

Above we used the `aria-required` property, this is the same as making an input **required** so the user cannot leave it blank. You should always use `required` in conjunction with `aria-required`. Remember that the 2 are not interchangeable, simply used together for a similar purpose.

<br>
<br>

---

## **Resources**

<br>
<br>

### Documentation

For a more complete guide with more examples, visit:
https://developer.mozilla.org/en-US/docs/Web/HTML/Element_

<br>

Or

<br>

### Tools

-   HTML validator &rarr; [Validator](https://validator.w3.org/nu/#textarea)

-   Images &rarr; [Unsplash](https://unsplash.com/) | [Pexels](https://www.pexels.com/)

-   Image compressor &rarr; [Squoosh](https://squoosh.app/)

-   Icons &rarr; [Fontawesome](https://fontawesome.com/) | [Heroicons](https://heroicons.com/) | [Phosphoricons](https://phosphoricons.com/)_(science icons)_

<br>
<br>

---
