# **Project Guidelines**

<br>

## Overview

Anytime I start a new project, I will refer to this doc as a general guideline of all the things I should make sure I check and do at the beginning and the end of the project.

<br>
<br>

---

## **Starting a new project**

If you're starting a new project, remember to check this list off first before progressing too much.

<br>

-   Review design guide

-   Create a title
-   Create a color palette
-   Create breakpoints
-   Create a reset stylesheet
-   Link a JavaScript file and use `strict mode`

<br>
<br>

#### **`Review design guide`**

Before starting a project, quickly review the [website personalities](css.md#design) section of the css guide to start with a good focus and approach.

<br>
<br>

#### **`Creating a title`**

A title should be long and meaningful... <mark>**finish this**</mark>

<br>
<br>

#### **`Creating a color palette`**

Use websites such as blah aand blah and check contrast... <mark>**finish this**</mark>

To start, choose three colors for your palette: a main (or `primary`) color, `secondary` color, and `accent` color. Then, use the `60/30/10` rule to apply these colors in your website design. According to this rule, <mark>60% of the color used should be the main color, 30% the secondary color, and 10% the accent color.</mark>

<br>
<br>

#### **`Create breakpoints`**

Use common breakpoints to ensure accessibility across all devices. The most popular web browsing device is mobile and then desktop, with tablets taking last place by a significant amount.

_Refer to [breakpoints](css.md#breakpoints) in the css guide._

<br>
<br>

#### **`Reset stylesheet`**

Consider adding the following styles to create a `reset` stylesheet.

```css
* {
    box-sizing: border-box;
}

html,
body,
div,
span,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
a,
address,
cite,
code,
img,
ol,
ul,
li,
form,
label,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
figure,
figcaption,
footer,
header,
menu,
nav,
section,
mark,
audio,
video {
    margin: 0;
    padding: 0;
    border: 0;
}

body {
    line-height: 1.5;
    color: #242424; /* Some sort of dark grey, not black*/
}

a:hover,
a:active {
  text-decoration: none;
}

ol,
ul {
    list-style: none;
}

table {
    border-collapse: collapse;
}

color-scheme: light; /* Indicates that the content is optimized for the "light" color scheme */
font-synthesis: none; /* Controls how font weights are synthesized when the specified font family lacks the requested font weight */
text-rendering: optimizeLegibility; /* Instructs the browser to use additional rendering techniques that improve the sharpness and clarity of text. */
-webkit-font-smoothing: antialiased; /* For WebKit-based browsers (Safari, Chrome on macOS), controls font smoothing and antialiasing. "antialiased" improves font rendering by  smoothing the jagged edges of characters. */
-moz-osx-font-smoothing: grayscale; /* For Mozilla Firefox on macOS, affects font smoothing and antialiasing. Grayscale antialiasing effect to improve font rendering. */
-webkit-text-size-adjust: 100%; /* Primarily for mobile, prevents browser from adjusting text size when user changes their browser's text size settings. Helps maintain original layout and design of the webpage. */
```

However, using the `*` selector to reset styles such as padding and margin is considered a bad practice, since it can lead to unexpected behaviour.

[More on resetting the default browser styles...](https://www.webfx.com/blog/web-design/css-tip-1-resetting-your-styles-with-css-reset/)

<br>
<br>

## **During the project**

Now that the essential starting points are out of the way, here are the things to keep in mind while working on the project.

<br>

-   Make feature branches / commits after initial markup is done

-   Add a lot of whitespace to separate sections (`200px` isn't too much)

-   When picking icons, pay attention to their designed optimal size (ex: `24px`).

-   When you use `display: flex` make sure to `align-items` as well

-   Set **very** visible background colors while designing, such as <mark style="background-color: red">red</mark>, <mark style="background-color: purple">purple</mark> and <mark style="background-color: blue">blue</mark>. This will help you see elements that would otherwise be invisible on the webpage. Avoid light shades of orange and green since those represent margin and padding respectively.

<br>
<br>

#### **`Feature branches`**

After the initial ...<mark>**finish this**</mark>

<br>
<br>

## **Finishing the project**

Now that the project is nearing its final stages, here are a few things to check off to make sure it's really ready!

<br>

-   Use lighthouse to check optimization
-   Do something...<mark>**finish this**</mark>

<br>

#### **`Lighthouse`**

Lighthouse can be used to check ...<mark>**finish this**</mark>

<br>
<br>

---
