# **Svelte**

<p style='color: #FFFFAC'>To be added: expressions, props, events, conditionals, loops, binding, etc...</p>

> _"Svelte makes it easy to create fast, reactive web apps without having to think about complex abstractions."_
>
> \- _Rich Harris_

<br>

> _"Svelte makes a huge difference in the effort required to make a web app. It makes the apps much faster and easier to write, without sacrificing flexibility or performance."_
>
> \- _Chris Fritz_

<br>
<br>

## Overview

**Svelte** _(slender, elegant)_ is a compiler _(not a framework)_ to create and ship highly optimized code quickly. I use this paired with **Vite** _(French for 'fast', used to host and refresh the local page)_ to rapidly create, test and deploy web apps. Since the documentation for Svelte is pretty good, this _guide_ will be more of a cheat sheet than anything. It will hold reminders and common syntax that will be useful for daily operations. This will serve as a reference point for all things Svelte. I won't be using **SvelteKit** for the foreseeable future, so I'll only be covering core Svelte Syntax.

<br>

The material I've found is a mixture of:

-   A [Udemy Svelte course](https://www.udemy.com/course/sveltejs-the-complete-guide/) by Maximillian Schwarzmuller _(It's a bit outdated and uses sapper, but most of it is fantastic)_.

- The official [Svelte site](https://svelte.dev/)

- The [You.com youchat](https://you.com/search?q=who+are+you&tbm=youchat&cfr=chat) bot _(A.I)_, it's not always accurate but a **huge** help during researching.

- Other various websites (Stack Overflow, Discord channels, etc)...

<br>

## **Quick tips & tricks**

-   Run `npm create svelte@latest app-name` **or** `npm create vite@latest app-name`_(vite)_ in your terminal to quickly create a web app.

- ⚠ Always remember to `npm install` before working on a project!

<br>
<br>

---

## **Fundamentals**

This section will hold the core fundamentals of Svelte.

<br>

#### **Setup**

Svelte files have **javascript** _(`<script>`)_, **css** _(`<style>`)_ and **html** sections. Technically, all sections are optional. I've tried to find the "recommended" order of these tags, but it seems the only convention is JavaScript always being on top. I haven't run into any issues with HTML and CSS being in either order. In the Svelte tutorial however, they put html last.

```html
<script>
    // JavaScript here
</script>

<style>
    /* CSS here */
</style>


<!-- HTML here -->
```

<br>
<br>

#### **Tags**

Regular html tags are the same, like `<div>`, written in lowercase. A capitalised tag such as `<Button>`, indicates a component.

```html
<script>
	import Button from './Button.svelte';
</script>

<div>
    <!-- Custom Component -->
	<Button />
</div>
```

<br>
<br>

#### **Section**

finish me...

```

```

<br>
<br>

#### **Section**

finish me...

```

```

<br>
<br>

#### **Section**

finish me...

```

```

<br>
<br>

#### **Section**

finish me...

```

```

<br>
<br>

#### **Section**

finish me...

```

```

<br>
<br>

#### **Section**

finish me...

```

```

<br>
<br>

---

## **Resources**

<br>
<br>

#### **Documentation**

For a more complete guide with more examples, visit:

<br>

- [Svelte.dev](https://svelte.dev/) - Official website and documentation

- Youtube, they have great videos that can help.

<br>
<br>

---
