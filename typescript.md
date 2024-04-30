# **Typescript**

> _"TypeScript is a typed superset of JavaScript that compiles to plain JavaScript."_
>
> -TypeScript Documentation

> _"TypeScript is like adding training wheels to your JavaScript programming."_
>
> -John Papa

<br>
<br>

## **Overview**

This guide is created as a reference point for TypeScript syntax, tips and best practices.

<br>

The material I've found is a mixture of:

- Udemy, [TypeScript course](https://www.udemy.com/course/learn-typescript/) by Colt Steele

- You.com [youchat](https://you.com/search?q=who+are+you&tbm=youchat&cfr=chat), an A.I. that helps you research the web.

- StackOverflow

- YouTube

- A.I. (_Bing, CgatGPT, Gemini_)

- Other various websites...

---

<br>

## **Quick tips & tricks**

- Quickly test out TypeScript in an [online playground](https://www.typescriptlang.org/play).

- In your terminal (with Node.js and TypeScript installed) type `tsc <file_name>` to compile to `JS`.

<br>
<br>

---

## **Fundamentals**

This section will hold the core fundamentals of Typescript, such as variable declaration with type annotation, annotating function parameters, implicit type inferring, etc.

<br>

#### **What is TypScript**

TypeScript(_TS for short_) is a superset of JavaScript(_JS for short_), meaning 100% of JS code is valid TS. Once your TS code is compiled, it becomes JavaScript again. This means that TS is for the developer, it's for coding, but the browser will only understand JS (_after it's compiled_). TS will also help you by giving you warnings **before runtime** in your editor.

An example of this is trying to change the type of a variable, e.g. a string to a number. TS will give you _red squigglies_ to show you that this should be avoided. So TS helps the developer write more efficient and safe JavaScript code, while annotating types when necessary (_we'll see **when** to use type annotation later on_).

#### **Type Annotation**

In TypeScript, you should avoid implicit type coercion, meaning when you declare a variable as a specific type (_eg: string or number_), it should remain that type. If you try to change a `string` to a `number`, it will raise an error. It will **not** prevent the code from running, as long as it's valid **JavaScript**. But will give you a warning in your editor and during compilation in your terminal. It's also worth noting that the **type** should be written in lowercase, such as `string`.

<br>

```ts
let jsExample1 = 'Hello World!';
let tsExample1: string = 'test'; // Annotating the variable type as string.

jsExample1 = 100; // JavaScript has no problem with this.
tsExample1 = 100; // TypeScript will raise an error
```

![TypeScript raising an error in VS Code](./img/ts/typeError.png)

<br>

```ts
let tsExample2: number = 5; // Annotating the variable type as number.
tsExample2 = '100'; // Raises an error, converting number to string.

let tsExample3: boolean = true;
tsExample3 = false; // No issues here
tsExample3 = 'true'; // Raises an error, converting boolean to string.
```

_**\*** TypeScript will also raise an error if you attempt to use a method on the wrong type; E.g. `5.toUpperCase()` **\***_

<br>
<br>

#### **Type Inference**

TypeScript is pretty smart, so you won't always have to explicitly declare your data type. Meaning it's not always necessary to use `let <variableName>: <type> = <value>`. Instead, you could simply declare the variable the same way you would in regular JavaScript syntax, and TypeScript will use **type inference** to determine what the correct type is.

<br>

```ts
let num = 5;
num = '100'; // Raises an error, converting number to string.
```

![TypeScript raising an error in VS Code](./img/ts/typeError2.png)

<br>
<br>

#### **The Any Type**

The `any` type turns off type checking for that variable, which is basically like going back to JavaScript. It also won't raise errors if you attempt to use a method on the wrong type. For instance, a **string** method on an **array** or a **number**. For the most part, this should be avoided unless you absolutely need to use it.

<br>

```ts
let variable: any = 'The answer to life, the universe and everything.';
variable = 42; // No problem with this

let otherVariable; // This also isn't great, it implicitly becomes 'any' type.
let otherVariable: string; // Still undefined, but annotates what type it will be later.
```

<br>
<br>

#### **Function Parameter Type Annotation**

When you define a function, if you don't specify the type of the parameters, they will implicitly have an `any` type. This brings you back to the stone age days of JavaScript and means that you can attempt to call a variable that holds a string (_or some other primitive value_) as if it were a function. 

```ts
  // Here we expect someVariable to be a string, but it isn't specified.
function someFunction(someVariable) {
  someVariable(); // But you passed a string...
}

// Proper way
function someFunction(someVariable: string) {
  someVariable(); // Error -> Type 'string' is not assignable to type 'number'.
}
```
<br>
<br>

#### **Return Type Annotations**

You can and in my opinion, should, specify the type of the returned value of your function. For instance if you have a function that logs a message to the console, that does not return any data. But if you have a function that multiplies 2 numbers, then that should always return a number. In both cases you should annotate the return value type. It isn't necessary but it's a clear way to say "hey, this function gives you this data" and also helps other developers understand your code faster.

```ts
  // This error logging fn never returns a value, so, its return is of type void. Void means void of data.
function logError(err: string): void {
  console.log(err);
}

// This function is used to multiply numbers so it will always return a number,
function MagicalMultiplyMachine(num1: number, num2: number) {
  return num1 * num2;
}
```

There's also the TypeScript specific `never` type which specifies values that **never** occur. It's not used as commonly and is used in functions that always throw an exception or are infinite loops. Unlike the type `void` which denotes no return value(_null or undefined behind the scenes_), but is in itself a data type, **never** means the function will never get the chance to return a value. The example below is from Colt Steele's Udemy course "Mastering TypeScript - 2024 Edition".

```ts
function makeError(msg: string): never {
  throw new Error(msg);

  // This will raise an error because the function should never return anything
  return undefined // undefined as an example but can be anything.
}

// function should never stop
function gameLoop(): never {
  while(true) {
    console.log("GAME LOOP RUNNING!");
  }

  // Return statement here would once again raise an error.
}
```

<br>
<br>

#### **Objects**

When creating an object in TypeScript, you should annotate each property type. The same applies to a function parameter object. This will help developers know what properties that object should contain and will raise an error if you attempt to modify a property that does not exist. Soon, we'll see how [type aliases](#type-aliases) improve this process.

```ts
  // First we annotate the property types and then we define the actual object literal.
  const humanTraits: {eyeColor: string, name: string} = {
    eyeColor: 'brown',
    name: 'Mario'
  };

  // We could also specify a default value here if we wanted e.g. fnName(obj: {prop: string} = {prop: 'blah'})
  function someFuncExpectingAnObj(someObj: {someProp: number, someOtherProp: number}): number {
    return someObj.someProp + someObj.someOtherProp;
  }

  // When an object is expected to be returned
  function humanBuilder(fName: string, lName: string, userAge: number): {name: string, age: number} {
    return {
      name: `${fName} + ${lName}`,
      age: userAge,
      unexpectedProp: 'Uh oh!' // Error: Object literal may only specify known properties, and 'unexpectedProp' does not exist in type '{ name: string; age: number; }'.
    }
  }
```

<br>

##### **Nested Objects**
Nested object type annotation behaves the same way as regular objects do.

```ts
  function nestedExample(nest: {someProp: string, objAsProp: {nestedProp: number, anotherNestedProp: string}});

  // Same code, maybe easier to read
  function nestedExample(nest: {
    someProp: string,
    objAsProp: {
      nestedProp: number,
      anotherNestedProp: string
      }
    });
```

<br>

##### **Optional Properties**
You can also create optional properties which allow you to specify properties that **may** be passed but don't **need** to be passed. This is achieved by placing a question mark (_`?`_) preceding the colon (_`:`_) like so:

```ts
// No error is raised since website is optional.
const cafes: {name: string, address: string, website?: string} = {
  name: 'Mr Roasters Fake Coffee',
  address: '123 fakestreet'
};
```

<br>

##### **Readonly Properties**
You can mark a property as **read only** in TypeScript using the special modifier keyword `readonly`. This does not exist in JavaScript, it's used in TypeScript to denote a property that should not change. A good example is an **id**, since those are usually unique and fetched from a database and not modified afterwards, we only read its value, we don't **write** to it. I use a [type alias](#type-aliases) in this example, these are covered below.

```ts
  // Quick example without using a type alias.
  const example: {readonly propName: string} = {
    propName: 'some value'
  };

  // Using a type alias
  type Game = {
    readonly serialNumber: string;
    readonly title: string;
    hoursPlayed: number;
  };

  // Object adhering to the Game type standard
  const witcher: Game = {
    serialNumber: 'tossacoin2urwitcher',
    title: 'The Witcher',
    hoursPlayed: 0
  };

  console.log(witcher.title); // Outputs witcher
  witcher.title = 'Da Witcha'; // Cannot assign to 'title' because it is a read-only property.
```

It's worth noting that if the readonly property is an object, you can still modify that object since it's a reference type (meaning it's still pointing to the same address in memory).

<br>
<br>

#### **Type Aliases**

Type aliases are very useful for creating the "blueprints" for a desired object structure. For instance, if you have multiple objects that expect exactly 2 properties of type number, there's no need to repeatedly define that each time. Instead, we can use a type alias to define what the object should look like, and then in the future we simply refer to that type alias when we want an object to contain those properties.

```ts
// Let's pretend this is an object structure we realize we reuse often
const basketballPoints: {redTeam: number, blueTeam: number} = {redTeam: 66, blueTeam: 84};
const soccerPoints: {redTeam: number, blueTeam: number} = {redTeam: 2, blueTeam: 3};
const hockeyPoints: {redTeam: number, blueTeam: number} = {redTeam: 1, blueTeam: 0};
```

There's no explicit TypeScript rule that specifies that a type alias must be defined in the upper camelcase naming convention, but this is the common convention so it's best to follow what the community is already using. So type aliases should start with a capital letter.

```ts
// This time we use a type alias, using the TypeScript specific keyword: 'type'.
type TeamPoints = {
  redTeam: number;
  blueTeam: number;

  // Note that commas are also accepted instead of semicolons, but semicolons are recommended for consistency with interface definitions.
  // redTeam: number,
  // blutTeam: number
};

// Now we refer to the TeamPoints type
const basketballPoints: TeamPoints = {redTeam: 66, blueTeam: 84};
const soccerPoints: TeamPoints = {redTeam: 2, blueTeam: 3};
const hockeyPoints: TeamPoints = {redTeam: 1, blueTeam: 0};

// Lets pretend we know which team is which, we see that the same rules apply to function parameters.
function pointCalculator(team1: {name: string, points: number}, team2: {name: string, points: number}): TeamPoints {
  return {
    redTeam: team1.points,
    blueTeam: team2.points
  }
}

// Not as useful but also possible to create a type alias for a primitive type
type ThisIsAString = string;
let someString: ThisIsAString = 'Hello from the past!';
someString = 47; // Type 'number' is not assignable to type 'string'
```

<br>
<br>

#### **Intersections**

Intersections ...

```ts
// TODO:
```

<br>
<br>

---

## **Resources**

<br>
<br>

#### **Tools**

- [TypeScript Playground](https://www.typescriptlang.org/play), for quickly testing and practicing TypeScript (_also has examples_).

<br>
<br>

#### **Documentation**

For a more complete guide with more examples, visit:

<br>

- [Typescriptlang.org](https://www.typescriptlang.org/docs/) - Official TypeScript documentation.

<br>
<br>

---
