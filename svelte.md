# **Svelte**

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

**Svelte** _(slender, elegant)_ is a compiler _(not a framework but referred to as a web framework more than a js framework, with a focus on enhancing html)_ to create and ship highly optimized code quickly. I use this paired with **Vite** _(French for 'fast', used to host and refresh the local page)_ to rapidly create, test and deploy web apps. Since the documentation for Svelte is pretty good, this _guide_ will be more of a cheat sheet than anything. It will hold reminders and common syntax that will be useful for daily operations. This will serve as a reference point for all things Svelte. I won't be using **SvelteKit** for the foreseeable future, so I'll only be covering core Svelte Syntax.

_These notes are based on Svelte 3 and have not been updated for over a year. Svelte 4 introduces some changes but most are not breaking changes. Svelte 5 introduces runes and other breaking changes. Remember to follow the official docs and read up on Svelte 5 here [Svelte 5 preview](https://svelte-5-preview.vercel.app/docs/introduction)_

<br>

The material I've found is a mixture of:

-   A [Udemy Svelte course](https://www.udemy.com/course/sveltejs-the-complete-guide/) by Maximillian Schwarzmuller _(It's a bit outdated and uses sapper, but most of it is fantastic)_.

- The official [Svelte site](https://svelte.dev/)

- The [You.com youchat](https://you.com/search?q=who+are+you&tbm=youchat&cfr=chat) bot _(A.I)_, it's not always accurate but a **huge** help during researching.

- Real-World Svelte Book by Tan Li Hau

- frontendmasters.com blog post: [Introducing svelte 5](https://frontendmasters.com/blog/introducing-svelte-5/#:~:text=Not%20only%20are%20there%20more,look%20for%20your%20next%20project.)

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

Svelte files have **javascript** _(`<script>`)_, **css** _(`<style>`)_ and **html** sections. Technically, all sections are optional. I've tried to find the "recommended" order of these tags, but it seems the only convention is JavaScript always being on top. I haven't run into any issues with HTML and CSS being in either order. In the Svelte tutorial however, they put html last, I personally always put my style tags on the bottom. All svelte files have a `.svelte` extension.

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

### **Tags**

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

### **Styling**

Svelte offers a few different ways to add styling to your components. Each have their use case and can be beneficial in the right scenario.

- **Global CSS:** Standard approach of having one external CSS file that is linked to your `index.html` file (_or imported via javascript e.g. `import './app.css';`_) which applies to all components. Good for general styling and css reset.

- **Module CSS:** These are files that have the `.module.css` extension, they work together with other module css files, meaning all files with `.module.css` extension will share styles, but will not affect components that do not use the css files.

- **Style block:** The most common approach in my opinion, styles are written between style tags of the component and **only apply to that module**, even if the same class names or selectors are targetted in another file. This is due to **fingerprinting** which svelte does while compiling all the code. It will add unique identifiers at the end of all classes to avoid name conflicts, but you don't need to worry about that, you can simply reuse the same class name across different files.

- **Inline CSS:** This is not unique to Svelte, but svelte offers a nice syntax to use inline css called the `style:css-property={value}` directive, which has higher precedence over regular inline CSS. Inline CSS in general has higher specificity than styles declared in a style block or external style sheet. These are good to use when you are conditionally applying a class based on a boolean condition.

```html
<script>
  // Importing style sheet, using an scss file as an example
  import './app.scss';

  // Importing module style sheet which are locally scoped with other module styles
  import './styles.module.css';

  // Used to conditionally apply classes
  let condition = true;

  // Used as the value for the color property
  let color = 'blue';
</script>

  <!-- Using a class from the style tags below -->
  <div class="class-name">...</div>

  <!-- Using a class from the module css file, the file is named 'styles' so we use 'styles.' -->
  <div class="styles.class-name">...</div>

  <!-- Traditional inline style syntax -->
  <p style="color: blue; font-size: 1.125rem;">Hello World</p>

  <!-- Inline style using the svelte style: directive -->
  <p style:color={color}>Hello World</p>

  <!-- Also acceptable if the style name matches the value -->
  <p style:color>Hello World</p> 

  <!-- You can also conditionally apply classes using the class: directive -->
  <p class:class-name={condition}>Hello World</p>

<style>
  .class-name {
    /* Styles */
  }
</style>
```

<br>

### **The `global()` pseudo-selector**

It's possible to make any style a global style by using the `global()` pseudo-selector. For styles defined within `<style>` tags, they will no longer be locally scoped.

```css
<style>
  /* :global(selector) */

  :global(a) {
    /* Some styles */
  }
</style>
```

<br>

### **Using custom properties**

You can also use custom properties to style your components. This is especially useful when you have one style that's applied across several files, such as the font size or color. When you return in the future and wish to make a change, you will need to locate every part of your code that uses that style, then update it. A better approach is to use a custom property, then you only need to change the value of that property and every file using it will be updated.

```css
/* Using root here will affect all elements, but not required */
:root {
  /* --property-name: value; */
  grey: #444;
  font-size-regular: 1rem;
}

/* Using the custom property */
p {
  color: var(--grey, grey); /* The second argument is a backup style just in case */
  font-size: var(--font-size-regular);
}
```

Svelte also allows you to set the styles of a component from outside of the component using custom properties. Let's say you have a component which uses the custom css property of `color`. You define this color in the component but you want to be able to set it from the outside. Svelte offers this syntax:

```html
  <!-- <CustomComponent --custom-property="new-value-here"/> -->
  <CustomButton --color="blue"/>

  <!-- Real-World Svelte book inspired example of the same code but less concise -->
  <div style="display: contents; --color: blue;">
    <CustomButton />
  </div>

  <!-- Note: "display: contents;" will style the element's children, ignoring the element/parent-->
```

<br>
<br>

### **Lifecycles**

All svelte components(_files_) go through 4 stages: initialization, mounting, updating and destroying. Svelte does not allow lifecycle functions to be called outside of the component initialization phase (_e.g. don't use `onMount()` inside of a callback function that triggers after the DOM is loaded and the user is interacting with an element_).

- **Initialization:** Your program is starting to run and code is being read from top to bottom, this prepares all of your code before inserting it into the DOM.

- **Mounting:** Your initializing/setup is now complete and elements are now being mounted into the DOM, this is where event listeners are attached to elements and svelte transitions occur (_mounting or removal of elements from DOM_). Svelte offers the `onMount()` hook(_function that extends svelte's native capabilities_) which runs code during the mounting phasze, after initialization.

- **Updating:** Svelte offers 2 hooks for DOM updates, `beforeUpdate()` and `afterUpdate()` which will run before or after an update is scheduled. For instance, you click something which updates a value (_In the real world of Svelte book, they use the example of clicking on a counter button which increments the count_), these hooks will either run immediately before the update happens, or directly after the update has finished. Unlike `onMount()` which usually runs once at the beginning, updates can happen many times.

- **Destroying:** When a component is removed from the DOM, it is "destroyed". So if there is a modal that is only visible after the user clicks something, then the user closes the modal, it enters the **destroying** lifecycle. Svelte offers the `onDestroy()` hook for this stage, which allows you to run code immediately before the element is destroyed (_cleanup_).

```svelte
<script>
  import { onMount, beforeUpdate, afterUpdate, onDestroy } from 'svelte';

  console.log('initializing'); // Runs first
  onMount(() => console.log('mounting')); // Runs second after initializing
  beforeUpdate(() => console.log('update starting')); // Runs before any update
  afterUpdate(() => console.log('update ended')); // Runs after any updates
  onDestroy(() => console.log('Destroying soon')); // Runs last, as it's removed
</script>
```

<br>
<br>

## **Svelte 4 & 5**
_This section was last updated Aug 2024, the rest of the guide was created for Svelte 3 and is outdated._

Below I'm going to cover the **highlights** of svelte 5. I will leave an example of the old syntax and new syntax. I will briefly touch on Svelte 4 but for the most part, Svelte 3 and 4 are the same (syntax), svelte 5 includes new syntax and Svelte 6-7 will likely begin to make some pre svelte 5 syntax obsolete.

<br>

### **Svelte 4**
Svelte 4 adopts modern tooling and drops support for some legacy versions of various technologies. The main changes that svelte 4 offers are performance related. The package size is reduced significantly resulting in faster `npm install`s, the JS output has also been reduced and transitions are now `|local` by default as opposed to `|global`. Here's a quote from the [svelte.dev](https://svelte.dev/blog/svelte-4) website.

> _"Svelte 4 is mainly a maintenance release, bumping minimum version requirements and tightening up the design in specific areas. It sets the stage for the next generation of Svelte to be released as Svelte 5 - we think you’ll love it."_

It's recommended to those on Svelte 3 to upgrade to Svelte 4 using Svelte's migration script `npx svelte-migrate@latest svelte-4` found here [Svelte 4 migration guide](https://svelte.dev/docs/v4-migration-guide). The script will update the required dependencies (_such as Typescript and Vite_) and even handle the transition scope (local|global) for you. It will remove `|local` since it's redundant and will insert `global` to avoid converting all transition to `local` if you choose to do so during the migration script. Most apps and libraries that are compatible with Svelte 3 should be ocmpatible with Svelte 4.

<br>

### **Svelte 5**
Svelte 5 addresses issues with earlier versions of svelte's reactivity system (_Stores and reactive variables were different reactivity systems_). It handles state in a new way, introduces signals, runes and makes some syntax deprecated. It also changes props, effects and custom events. It is a rewrite of the Svelte compiler and runtime and boasts more reliable reactivity. Although they're introducing features such as `runes(_signals_)` to replace `reactive statements` and `snippets` to replace `slots`, they are not removing the older features just yet. Meaning, slots are still valid but they are marked as deprecated and will likely be removed in Svelte 6-7. The choice to not make them immediately obsolete was to ensure a fluid migration from 4 to 5.

<br>

### **Runes**
In web development, **signals** are one of the key primitives of reactive programming. By definition, they are generated **notifications** that are sent to a process when an event occurs. This means when a change happens, a signal is sent to notify other parts of the application of this change so they can update accordingly.


### **State**


### **Props**


### **Effects**

### **Snippets**


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
