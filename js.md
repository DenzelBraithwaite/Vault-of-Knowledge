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

This guide will serve as a reference point for JavaScript fundamentals, syntax, tips, tricks and best practices. For quick testing, you can use the console or one of many free websites that allow you to write and test code.

<br>

The material I've found is a mixture of:

-   Udemy - [The Complete JavaScript Course](https://www.udemy.com/course/the-complete-javascript-course/)

-   [MDN docs](https://developer.mozilla.org/en-US/)

-   [Stackoverflow](https://stackoverflow.com/)

-   [JS bin](https://jsbin.com/?js,console) _(For quickly testing code snippets)_

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

Functions are not a data type, they're a value. That's why we can store them in variables and use them in places that expect a value.

Function delcaration vs expression:

```js
// function declaration
function functionName(parameter) {
    // do something and or return something
}

// function expression
const functionName = function (parameter) {
    // do something and or return something
};

// Arrow functions
const functionName = parameter => {
    // Do something or return something
};
```

Function declarations are hoisted, so they can be used before they were declared, as opposed to function expression which requires the function to be defined before you can call it.

<mark>**finish this**</mark>

<br>
<br>

**Arrays**

<mark>**finish this**</mark>

<br>
<br>

**Array methods**

Arrays are zero indexed, meaning when you count the index of each item, you start at 0.

```js
const teaMenu = ['black', 'green', 'oolong', 'white', 'herbal'];

teaMenu.pop(); // Will remove the last item('herbal') from the array

teaMenu.push('yellow'); // Will add an item('yellow') to the end of the array

teaMenu.shift(); // Will remove the first item('black') from the array

teaMenu.unshift('black'); // Will add an item('black') to the beginning of the array

teaMenu.indexOf('oolong'); // outputs 2, black = 0, green = 1, oolong = 2

teaMenu.indexOf('guayusa'); // outputs -1 since the item does not exist in the array

teaMenu.includes('green'); // outputs true since the item exists in the array

teaMenu.length; // This is actually a property and not a method, it will return the length
```

<mark>**finish this**</mark>

<br>
<br>

## **Objects**

Objects have key - value pairs, the keys are also referred to as properties. The easiest way to create an object is by using the curly braces, this is called object literal notation.

```js
const denzel = {
    // Order doesn't matter, so the browser will display it in the console alphabetically, like this.
    age: 26,
    favoritecolors: ['teal', 'pink', 'purple']
    firstName: Denzel,
    friendly: true,
    lastname: Braithwaite,
};
```

<mark>**finish this**</mark>

<br>
<br>

### **Bracket notation vs dot notation**

You can access a property from an object by using either bracket or dot notation. The main difference is, when using square brackets, you can put any expression _(something that produces a value)_ between the brackets and it will work, but the same is not true for dot notation.

```js
const burger = {
    tomato: true,
    lettuce: true,
    onions: false,
    cheese: true,
    doublePatty: false,
    buns: true
};

const patty = 'Patty';

console.log(burger.tomato); // Outputs true
console.log(burger['double' + patty]); // Outputs false
console.log(burger.'double' + patty); // raises error: Unexpected String
```

<mark>**finish this**</mark>

<br>
<br>

**Adding properties**

```js
const burger = {
    buns: true,
    patty: true
};

// Adds the key/property tomato with a value of true.
burger.tomato = true;

// Adds the key/property onions with a value of false.
burger['onions'] = false;
```

<mark>**finish this**</mark>

<br>
<br>

**Adding a function to an object**

Any function that is attached to an object is called a `mthod`. You can create an object method by add a function expression as a value for an object's property. This works since a property expects a value, and an expression produces a value.

```js
const computer = {
    mouse: 'Awesome mouse',
    keyboard: 'gaing keyboard',
    speakers: 'broken speakers',

    repairSpeakers: function () {
        return (this.speakers = 'Brand new speakers');
    }
};

console.log(computer.repairSpeakers()); // Updates speakers property and outputs the value: 'Brand new speakers'

console.log(computer['repairSpeakers']()); // Updates speakers property and outputs the value: 'Brand new speakers'
```

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
