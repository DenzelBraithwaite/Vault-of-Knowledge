# **Markdown Language**

_Cheatsheet for .md syntax_

<br>

## **Overview**

Nearly all Markdown applications support the basic syntax outlined in the original Markdown design document. There are minor variations and discrepancies between Markdown processors — those are noted inline wherever possible.

<br>

## **Headings**

To create a heading, add number signs (#) in front of a word or phrase. The number of number signs you use should correspond to the heading level. For example, to create a heading level three (\<h3>), use three number signs (e.g., ### My Header).

# Heading level 1 <!-- Alt: <h1>Heading level 1</h1> -->

## Heading level 2 <!-- Alt: <h2>Heading level 2</h2> -->

### Heading level 3 <!-- Alt: <h3>Heading level 3</h3> -->

#### Heading level 4 <!-- Alt: <h4>Heading level 4</h4> -->

##### Heading level 5 <!-- Alt: <h5>Heading level 5</h5> -->

###### Heading level 6 <!-- Alt: <h6>Heading level 6</h6> -->

<br>

## Heading Best Practices

Markdown applications don’t agree on how to handle a missing space between the number signs (#) and the heading name. For compatibility, always put a space between the number signs and the heading name.

✅ Do this: `_# Heading_`  
❌ Don't do this: `_#Heading_`

<br>

## **Paragraphs**

To create paragraphs, use a blank line to separate one or more lines of text.

<!-- Or use <p> tags </p> -->

_Note: If you need to indent paragraphs in the output, see the section on how to indent (tab)._

✅ Do this: 'Hello World'  
❌ Don't do this: ' Hello World'

_Don't put tabs or spaces in front of your paragraphs, keep them left-aligned._

<br>

## **Line Breaks**

To create a line break or new line (\<br>), end a line with two or more spaces, and then type return.

## Line Break Best Practices

You can use two or more spaces (commonly referred to as “trailing whitespace”) for line breaks in nearly every Markdown application, but it’s controversial. It’s hard to see trailing whitespace in an editor, and many people accidentally or intentionally put two spaces after every sentence. For this reason, you may want to use something other than trailing whitespace for line breaks. If your Markdown application supports HTML, you can use the \<br> HTML tag.

_For compatibility, use trailing white space or the \<br> HTML tag at the end of the line._

✅ Do this: trailing 2 spaces`__` or `<br>`  
❌ Don't do this: ending sentence with `\`

<br>

## **Emphasis**

You can add **_emphasis_** by making text **bold** or _italic_.

<br>

## Bold

To bold text, add two asterisks or underscores before and after a word or phrase. To bold the middle of a word for emphasis, add two asterisks without spaces around the le**tt**ers.

### Bold Best Practices

Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold the middle of a word for emphasis.

<br>

## Italic

To italicize text, add one asterisk or underscore before and after a word or phrase. To italicize the middle of a word for emphasis, add one asterisk without spaces around the letters.

### Italic Best Practices

Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to italicize the middle of a word for emphasis.

✅ Do this: `A*cat*meow` --> A*cat*meow  
❌ Don't do this: `A_cat_meow` --> A_cat_meow

<br>

## Bold and Italic

To emphasize text with bold and italics at the same time, add three asterisks or underscores before and after a word or phrase. To bold and italicize the middle of a word for emphasis, add three asterisks without spaces around the letters.

_Note: The order of the em and strong tags might be reversed depending on the Markdown processor you're using._

### Bold and Italic Best Practices

Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold and italicize the middle of a word for emphasis.

✅ Do this: `This is really***very***important text.` --> This is really***very***important text  
❌ Don't do this: `This is really___very___important text.` --> This is really___very___important text.

<br>

## **Blockquotes**

To create a blockquote, add a > in front of a paragraph.

Example: `> I am a blockquote.`

Output:
> I am a blockquote.

<br>

## Blockquotes with Multiple Paragraphs

Blockquotes can contain multiple paragraphs. Add a > on the blank lines between the paragraphs.
```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

Output:
> Dorothy followed her through many of the beautiful rooms in her castle.
> 
>The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

<br>

## Nested Blockquotes

Blockquotes can be nested. Add a >> in front of the paragraph you want to nest.
```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> > The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```
Output:  
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> > The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

<br>

## Blockquotes with Other Elements

Blockquotes can contain other Markdown formatted elements. Not all elements can be used — you’ll need to experiment to see which ones work.

```
> #### The quarterly results look great!
>
> -   Revenue was off the chart.
> -   Profits were higher than ever.
>
>     _Everything_ is going according to **plan**.
```

Output:
> #### The quarterly results look great!
>
> -   Revenue was off the chart.
> -   Profits were higher than ever.
>
>     _Everything_ is going according to **plan**.

<br>

## Blockquotes Best Practices

For compatibility, put blank lines before and after blockquotes.

✅ Do this:
```
Try to put a blank line before...

> This is a blockquote

...and after a blockquote. Without blank lines, this might not look right.
```

❌ Don't do this:
```
Without blank lines, this might not look right.
> This is a blockquote
Don't do this!
```

<br>

## **Ordered Lists**

To create an ordered list, add line items with numbers followed by periods. The numbers don’t have to be in numerical order, but the list should start with the number one.

<br>

✅ Do this:
```
1. First item
2. Second item
3. Third item
4. Fourth item
    1. Tab or 4 spaces, use '1.' to start at 1.
    9. Doesn't matter what number you use afterwards
    3. It will count in order
20. Then stop nesting by removing tab / space
```
Output:
1. First item
2. Second item
3. Third item
4. Fourth item
    1. Tab or 4 spaces, use '1.' to start at 1.
    9. Doesn't matter what number you use afterwards
    3. It will count in order
20. Then stop nesting by removing tab / space

<br>

✅ Or do this:

```
<ol>
  <li>First item</li>
  <li>Second item</li>
    <ol>
        <li>First nested list item</li>
        <li>Second nested list item</li>
    </ol>
  <li>Third item</li>
  <li>Fourth item</li>
</ol>
```

Output:
<ol>
  <li>First item</li>
  <li>Second item</li>
    <ol>
        <li>First nested list item</li>
        <li>Second nested list item</li>
    </ol>
  <li>Third item</li>
  <li>Fourth item</li>
</ol>

<br>

## Ordered List Best Practices

CommonMark and a few other lightweight markup languages let you use a parenthesis ()) as a delimiter (e.g., 1) First item), but not all Markdown applications support this, 
so it isn’t a great option from a compatibility perspective. For compatibility, use periods only.

<br>

✅ Do this:
```
1. First item
2. Second item
```

❌ Don't do this:
```
1) First item
2) Second item
```

<br>

## Unordered Lists

To create an unordered list, add dashes (-), asterisks (*), or plus signs (+) in front of line items. Indent one or more items to create a nested list.

✅ Do this:
```
- First item
- Second item
- Third item
- Fourth item
    - Tab or 4 spaces, use '1.' to start at 1
    - Doesn't matter what number you use afterwards
    - It will count in order
- Then stop nesting by removing tab / space
```

Output:
- First item
- Second item
- Third item
- Fourth item
    - Tab or 4 spaces to start nesting another list
    - Second item
- Then stop nesting by removing tab / space

<br>

✅ Or do this:
```
<ul>
  <li>First item</li>
  <li>Second item</li>
    <ul>
        <li>First nested list item</li>
        <li>Second nested list item</li>
    </ul>
  <li>Third item</li>
  <li>Fourth item</li>
</ul>
```
Output:
<ul>
  <li>First item</li>
  <li>Second item</li>
    <ul>
        <li>First nested list item</li>
        <li>Second nested list item</li>
    </ul>
  <li>Third item</li>
  <li>Fourth item</li>
</ul>

<br>

## Starting Unordered List Items With Numbers

If you need to start an unordered list item with a number followed by a period, you can use a backslash (\) to escape the period.
```
-   1968\. A great year!
-   I think 1969 was second best.
```
Or
```
<ul>
  <li>1968. A great year!</li>
  <li>I think 1969 was second best.</li>
</ul>
```
Output:
-   1968\. A great year!
-   I think 1969 was second best.

<br>

## Unordered List Best Practices

Markdown applications don’t agree on how to handle different delimiters in the same list. For compatibility, don’t mix and match delimiters in the same list — pick one and stick with it.

✅ Do this:
```
- First item
- Second item
- Third item
- Fourth item
```
Output:
- First item
- Second item
- Third item
- Fourth item

<br>

❌ Don't do this:
```
+ First item
* Second item
- Third item
* Fourth item
```

<br>

## **Images**

```
Syntax: ![Alt message here](URL here)
Example: ![Image of lines of code](img/code_sample.png)
```
Output:  
![Image of lines of code](img/code_sample.png)

<br>

## Linking Images

To add a link to an image, enclose the Markdown for the image in brackets, and then add the link in parentheses.

<br>

Example: 
```
[![A snippit of a mountain photo from markdownguide.org](img/linked_img_sample.png "Shop rock mountain peak"
```

Output:  
![An old rock in the desert](/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers"

<br>

## **Horizontal Rules**

To create a horizontal rule, use three or more asterisks (***), dashes (---), or underscores (___) on a line by themselves.
The rendered output of all three looks identical:

## Horizontal Rule Best Practices

For compatibility, put blank lines before and after horizontal rules.

✅ Do this:
```
Try to put a blank line before...

---

...and after a horizontal rule.
```

<br>

❌ Don't do this:
```
Without blank lines, this would be a heading.
---
Don't do this!
```

<br>

## **Links**

To create a link, enclose the link text in brackets (e.g., [Duck Duck Go]) and then follow it immediately with the URL in parentheses (e.g., (https://duckduckgo.com)).

<br>

Example:
```
My favorite search engine is [Duck Duck Go](https://duckduckgo.com)
```

Output: My favorite search engine is [Duck Duck Go](https://duckduckgo.com).

<br>

## Adding Titles

You can optionally add a title for a link. This will appear as a tooltip when the user hovers over the link. To add a title, enclose it in quotation marks after the URL.

```
My favorite search engine is [Duck Duck Go](https://duckduckgo.com 'The best search engine for privacy').
```

Output: My favorite search engine is [Duck Duck Go](https://duckduckgo.com 'The best search engine for privacy').

<br>

## URLs and Email Addresses

To quickly turn a URL or email address into a link, enclose it in angle brackets.

<br>

Example:
```
<https://www.markdownguide.org>
<fake@example.com>
```

Output:
<https://www.markdownguide.org>
<fake@example.com>

<br>

## Formatting Links

To emphasize links, add asterisks before and after the brackets and parentheses. To denote links as code, add backticks in the brackets.

I love supporting the **[EFF](https://eff.org)**.
This is the _[Markdown Guide](https://www.markdownguide.org)_.
See the section on [`code`](#code).
The rendered output looks like this:

I love supporting the EFF.
This is the Markdown Guide.
See the section on code.

Reference-style Links
Reference-style links are a special kind of link that make URLs easier to display and read in Markdown. Reference-style links are constructed in two parts: the part you keep inline with your text and the part you store somewhere else in the file to keep the text easy to read.

Formatting the First Part of the Link
The first part of a reference-style link is formatted with two sets of brackets. The first set of brackets surrounds the text that should appear linked. The second set of brackets displays a label used to point to the link you’re storing elsewhere in your document.

Although not required, you can include a space between the first and second set of brackets. The label in the second set of brackets is not case sensitive and can include letters, numbers, spaces, or punctuation.

This means the following example formats are roughly equivalent for the first part of the link:

[hobbit-hole][1]
[hobbit-hole] [1]
Formatting the Second Part of the Link
The second part of a reference-style link is formatted with the following attributes:

The label, in brackets, followed immediately by a colon and at least one space (e.g., [label]: ).
The URL for the link, which you can optionally enclose in angle brackets.
The optional title for the link, which you can enclose in double quotes, single quotes, or parentheses.
This means the following example formats are all roughly equivalent for the second part of the link:

[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle
[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'
[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'
[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'
[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'
[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'
[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'

You can place this second part of the link anywhere in your Markdown document. Some people place them immediately after the paragraph in which they appear while other people place them at the end of the document (like endnotes or footnotes).

An Example Putting the Parts Together
Say you add a URL as a standard URL link to a paragraph and it looks like this in Markdown:

In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole](https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'), and that means comfort.
Though it may point to interesting additional information, the URL as displayed really doesn’t add much to the existing raw text other than making it harder to read. To fix that, you could format the URL like this instead:

In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'

In both instances above, the rendered output would be identical:

In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to eat: it was a hobbit-hole, and that means comfort.

and the HTML for the link would be:

<a href="https://en.wikipedia.org/wiki/Hobbit#Lifestyle" title="Hobbit lifestyles">hobbit-hole</a>
Link Best Practices
Markdown applications don’t agree on how to handle spaces in the middle of a URL. For compatibility, try to URL encode any spaces with %20. Alternatively, if your Markdown application supports HTML, you could use the a HTML tag.

✅ Do this ❌ Don't do this
[link](https://www.example.com/my%20great%20page)

<a href="https://www.example.com/my great page">link</a> [link](https://www.example.com/my great page)
Images
To add an image, add an exclamation mark (!), followed by alt text in brackets, and the path or URL to the image asset in parentheses. You can optionally add a title in quotation marks after the path or URL.

![The San Juan Mountains are beautiful!](/assets/images/san-juan-mountains.jpg 'San Juan Mountains')
The rendered output looks like this:

The San Juan Mountains are beautiful!

Note: To resize an image, see the section on image size. To add a caption, see the section on image captions.
Linking Images
To add a link to an image, enclose the Markdown for the image in brackets, and then add the link in parentheses.

[![An old rock in the desert](/assets/images/shiprock.jpg 'Shiprock, New Mexico by Beau Rogers')](https://www.flickr.com/photos/beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv)
The rendered output looks like this:

An old rock in the desert
Escaping Characters
To display a literal character that would otherwise be used to format text in a Markdown document, add a backslash (\) in front of the character.

\* Without the backslash, this would be a bullet in an unordered list.
The rendered output looks like this:

-   Without the backslash, this would be a bullet in an unordered list.

Characters You Can Escape
You can use a backslash to escape the following characters.

Character Name
\ backslash
` backtick (see also escaping backticks in code)

-   asterisk
    \_ underscore
    { } curly braces
    [ ] brackets
    < > angle brackets
    ( ) parentheses

# pound sign

-   plus sign

*   minus sign (hyphen)
    . dot
    ! exclamation mark
    | pipe (see also escaping pipe in tables)
    HTML
    Many Markdown applications allow you to use HTML tags in Markdown-formatted text. This is helpful if you prefer certain HTML tags to Markdown syntax. For example, some people find it easier to use HTML tags for images. Using HTML is also helpful when you need to change the attributes of an element, like specifying the color of text or changing the width of an image.

To use HTML, place the tags in the text of your Markdown-formatted file.

This **word** is bold. This <em>word</em> is italic.
The rendered output looks like this:

This word is bold. This word is italic.

## HTML Best Practices
For security reasons, not all Markdown applications support HTML in Markdown documents. When in doubt, check your Markdown application’s documentation. Some applications support only a subset of HTML tags.

Use blank lines to separate block-level HTML elements like \<div>, \<table>, \<pre>, and \<p> from the surrounding content. Try not to indent the tags with tabs or spaces — that can interfere with the formatting.

You can’t use Markdown syntax inside block-level HTML tags. For example, <p>italic and **bold**</p> won’t work.

For a more complete guide with more examples, visit: https://www.markdownguide.org/basic-syntax/