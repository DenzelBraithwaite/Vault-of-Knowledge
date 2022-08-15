# **CSS**

_Styling, designing & layouts._

<br>

## Overview

This file will contain all of the common CSS terminology and concepts with brief descriptions and examples.

<br>
<br>

___

## **Fundamentals**

<br>

![Screenshot of CSS cheatsheet](img/css/css_guide1.png)
![Screenshot of CSS cheatsheet](img/css/css_guide2.png)
![Screenshot of CSS cheatsheet](img/css/css_guide3.png)

<br>

___

## **Property references**

<br>

![Screenshot of CSS cheatsheet](img/css/css_guide4.png)
![Screenshot of CSS cheatsheet](img/css/css_guide5.png)
![Screenshot of CSS cheatsheet](img/css/css_guide6.png)
![Screenshot of CSS cheatsheet](img/css/css_guide7.png)
![Screenshot of CSS cheatsheet](img/css/css_guide8.png)
![Screenshot of CSS cheatsheet](img/css/css_guide9.png)
![Screenshot of CSS cheatsheet](img/css/css_guide10.png)
![Screenshot of CSS cheatsheet](img/css/css_guide11.png)
![Screenshot of CSS cheatsheet](img/css/css_guide12.png)
![Screenshot of CSS cheatsheet](img/css/css_guide13.png)
![Screenshot of CSS cheatsheet](img/css/css_guide14.png)
![Screenshot of CSS cheatsheet](img/css/css_guide15.png)
![Screenshot of CSS cheatsheet](img/css/css_guide16.png)

<br>

___

## **Knowledge base**

<br>

## Selectors

One of the key initial concepts in CSS is selectors and how they work. From there you can move into advanced selectors and pseudoselectors, as well as understanding the various types of properties you can manipulate. But without selectors, you have no way to apply the things you learn, so this is where you start.

<br>

#### **`ID selector`**

ID selectors are the most powerful type of selector in terms of CSS specificity. Meaning that they beat out other types of selectors and the styles defined within win. That sounds good, but that’s typically considered bad, because it’s nice to have lower-specificity selectors that are easier to override when needed.

<br>

#### **`Class selector`**

Class selectors are your friend. They are probably the most useful and versatile selectors out there. In part because they are well supported in all browsers. In part because you can add multiple classes (just separated by a space) on HTML elements. In part because there are JavaScript things you can do specifically for manipulating classes.

<br>

#### **`Tag selector`**

<mark>Tag selectors are at their most useful when changing properties that are unique to that HTML element.</mark> Like setting the list-style on a \<ul> or tab-size on a \<pre>. Also in reset stylesheets where you are specifically trying to unset styles that browsers apply to certain elements.

Don’t rely on them too much though. It’s typically more useful to have a class define styling that you can use on any HTML element.

<br>

#### **`Class selector`**

ID selectors are the most powerful type of selector in terms of CSS specificity. Meaning that they beat out other types of selectors and the styles defined within win. That sounds good, but that’s typically considered bad, because it’s nice to have lower-specificity selectors that are easier to override when needed.

<br>

#### **`Class selector`**

ID selectors are the most powerful type of selector in terms of CSS specificity. Meaning that they beat out other types of selectors and the styles defined within win. That sounds good, but that’s typically considered bad, because it’s nice to have lower-specificity selectors that are easier to override when needed.

<br>

#### **`Class selector`**

Class selectors are your friend. They are probably the most useful and versatile selectors out there. In part because they are well supported in all browsers. In part because you can add multiple classes (just separated by a space) on HTML elements. In part because there are JavaScript things you can do specifically for manipulating classes.








<br>
<br>

## FAQ

<br>

## What is Span in CSS and what is it used for?

Span is a pretty simple, but useful tool for developers and designers. It's very similar to visisions, with on key difference: no linebreak is created when a span is used. Spans are an inline element and not a block level element. Yu can use the span tag to augment certain areas of text in your content.

<br>

Exmaple:  
```
/* CSS */

.italic {
    font-style: italic;
}


<!-- HTML -->

<span class="italic">This text shall be italic!</span>
```

Output:
> _This text shall be italic!_

<br>

## What are the different types of CSS?

<br>

### 1. Inline Styles

These are the tags that are used within the actual HTML as opposed to an external CSS stylesheet.

<br>

### 2. Embedded Styles

These are the tags that are used in the head section of your HTML document. These only affect the tags on the page they’re embedded in.

<br>

### 3. External Styles

Finally, we have the codes that are used in a separate style sheet that is externally saved and attached to your website.

<br>

<br>
<br>

_For a more complete guide with more examples, visit: https://zendev.com/ultimate-guide-to-learning-css.html#comprehensive-resources_

___
