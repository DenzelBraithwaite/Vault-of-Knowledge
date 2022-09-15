# JavaScript

> _JavaScript: Don't judge me by my bad parts, learn the good stuff and stick with that!_
>
> -Eric Freeman

> _"There's almost nothing that you can't build after getting really good at JavaScript, inside or outside of the browser."_
>
> -Jonas Schmedtmann

<br>
<br>

## Overview

This guide will serve as a reference point for JavaScript fundamentals, syntax, tips, tricks and best practices.
_Fundamentals, syntax, tips, tricks and best practices_

<br>

The material I've found is a mixture of:

-   Udemy - [The Complete JavaScript Course](https://www.udemy.com/course/the-complete-javascript-course/)

-   MDN docs

-   Stackoverflow

-   Other various websites

<br>
<br>

---

## **Notes to be sorted later**

Comment out code with `//` for a single line comment, or a multi-line code with `/**/`, like `CSS`

<br>
<br>

Use `typeof` to deterine a data type's value.

<br>
<br>

Creating an undefined variable:

```js
let variableName;
```

<br>
<br>

If you `typeof null` the console will tell you it's an `object`, but this is a bug in JavaScript that's not corrected for legacy reasons.

If you use `typeof NaN` the console outputs 'Number', so "_Not a number_" is technically a number.

<br>
<br>

`var` vs `let` vs `const`:
`var` is the old way with global scope<mark>**finish this**</mark>

`let` is a new way to declare a variable with a smaller scope. let creates a variable that can be reassigned.<mark>**finish this**</mark>

`const` is a new way to declare a variable with a smaller scope. You cannot reassign a `const` variable. a `const` variable cannot be empty, it needs an initial value. Always decalre variables with `const` unless you know the variable will change, this can reduce the risk of potential bugs.<mark>**finish this**</mark>

Extra: You could also technically write `phoneType = 'iPhone'` without the use of a `keyword` such as `let` or `const` and it would seem like it still worked, but this would create a property on the `global object` and not a variable in your local scope.

<br>
<br>

**operators**

Arithmetic operators: `+ - * / **` also `+= -+ *= /= **= ++ --` and `> < >= <= ===`

`+`

`-`

`*`

`/`

`**`

`---`

<br>

`==` and `!=` vs `===` and `!==`

`==` is the loose loose operator, `===` is the strict equality operator. `==` does type coercion, so it should be avoided. `===` does not perform type coercion so it's less liekly to introduce a bug.

```js
if ('18' == 18) Console.log('Looks the same!');
// This will be treated as 'true'

if ('18' === 18) Console.log('Looks the same!');
// This will be treated as 'false'
```

`!=` and `!==` are the **opposite** of the equality operator, these are `different` operators. In plain English, it means "is not equal to" as opposed to "Is equal to"

<br>

[JS operator precedence, scroll down and reference table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)

<br>
<br>

**The `&&(and), ||(or)` and `!`**

```js
const hasVision = true;
const hasHearing = true;
const hasLegs = false;

console.log(hasVision && hasHearing);
// Outputs: true

console.log(hasVision && hasLegs);
// Outputs: false

console.log(hasVision || hasLegs);
// Outputs: true

console.log(hasVision && hasHearing && !hasLegs);
// Outputs: true
```

**String concatenation** <mark>**finish this**</mark>

```js
const num = 5;
console.log('Hey ' + "I'm" + num + ' years old.');
```

**String template literals** <mark>**finish this**</mark>
Use template literals to create multi-line strings. Template literals expect `expressions` not `statements`.

```js
const num = 5;
console.log(`Hey I'm ${num} years old.`);

console.log(`${let num = 5}`) // Don't use a statement, this will raise an error.
```

<br>
<br>

**Conditionals**

if statements:

```js
if (4 >= 5) {
    const magicNumber = 4;
    console.log(magicNumber);
    // Output: 4, but this code won't execute.
} else {
    const magicNumber = 5;
    console.log(magicNumber);
    // Output: 5, this code WILL run
}

if (true === true) console.log('This is also valid syntax');

if (true === false) {
    console.log("This won't run");
} else if (true) {
    console.log('This will run');
} else {
    console.log("This won't run");
}
```

The `conditional ternary operator (?)` is used to write a conditional statement in one line.

```js
const numOfBeers = 6;
numOfBeers <= 3 ? console.log('Drive home safely') : console.log('Take a cab');
```

<br>
<br>

`Type conversion vs coercion`

Conversion is when you explicitly want to convert one data type to another. Like changing a string to a number.

```js
const year = '2022';
console.log(typeof Number(year));
// Outputs
```

Coercion is when JavaScript implicitly converts a data type for you, such as concatenating strings and numbers turns numbers into a string.

```js
console.log(`This is a random number ${5}5`);
//  Outputs: 'This is a random number 55', JS converts the number to a string

console.log('5' - 5);
// Outputs: 0, JS converts the string to a number

console.log(1 + 2 + 3 + '4');
// Outputs: 64, when it reaches the string, it converts it.
```

<br>
<br>

**Falsy values**

1. false (boolean)
2. 0 (number type 0)
3. '' (empty string)
4. undefined
5. null
6. NaN

All other values are **_truthy_**

<br>
<br>

**Switch statement** <mark>**finish this**</mark>

```js
const food = 'salad';

switch (food) {
    case 'spaghetti': // if (food === 'spaghetti')
        console.log('Yay, spaghetti for supper today!');
        break;
    case 'burgers':
        console.log('Yay, burgers for supper today!');
        break;
    case 'salad':
        console.log('Aww, salad for supper today...');
        break;
    default:
        console.log("I gotta figure out what I'm eating today");
}
```

<br>
<br>

**`Expression` vs `Statements`**

An expression is a piece of code that produces a value.

```js
3 + 4; // This is an expression
2020; // This is an expression
true && true; // This is an expression
```

If declarations are complete senteces, expressions are like words that make-up that sentence.

```js
if (true) {
    const variableName = "Doesn't matter"; // This is a statement, doesn't produce any value.
}
```

<br>
<br>

**Strict mode**
Use strict mode by adding one line to the top of you js file. It must be the very first line (excluding comments, since they're ignore). This will forbid you from doing certain things and it will also raise visible errors in the console instead of failing silently.

Strict mode will also forbid the use of certain variable names if those names are reserved for future features / keywords that might be released.

```js
'use strict';
```

<mark>**finish this**</mark>

<br>
<br>

**Functions**
Leave notes on all ways to create a function, how to call a function, what higher functions are, the return keyword, etc.

<mark>**finish this**</mark>

<br>
<br>

## **Fundamentals**

This will hold the fundamentals...<mark>**finish this**</mark>

<br>
<br>

### **Linking a JS file**

There are a few ways to link a...<mark>**finish this**</mark>

1. Using `<script>` tags.

2. Using a `style.js` file and linking it in your `html` file at the bottom of the `<body>`.

```js
<script src="script.js"></script>
```

<br>
<br>

### **Primitive data types**

...<mark>**finish this**</mark>

<br>
<br>

#### **`Values & Variables`**

In JavaScript, every value is either an object or a primitive value. A value is only primitive if it's not an object.

There are 7 types of primitive data in JavaScript:

1. Number (Floating point numbers, always have decimals)
2. String (Sequence of characters in single or double quotes)
3. Boolean (true or false)
4. Undefined (variable declared with an empty value)
5. Null (no valuem similar to undefined)
6. Symbol (unique value that can't be changed)
7. BigInt (ES2020, supports larger integers than the `number` type)

...<mark>**finish this**</mark>

<br>

#### **`...`**

...<mark>**finish this**</mark>

<br>

#### **`...`**

...<mark>**finish this**</mark>

<br>

---

## **Resources**

<br>

Udemy - [The Complete JavaScript Course](https://www.udemy.com/course/the-complete-javascript-course/)
