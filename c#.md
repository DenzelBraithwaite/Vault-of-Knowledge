# **C Sharp (C#)**

> _"It is important that you remember your programs are actually executed by a piece of hardware which has physical limitations."_
>
> Rob Miles (_author of The C# Programming Yellow Book_)

<br>
<br>

## Overview

This guide is focused on all notes related to **C#** and **.net**. Whenever relevant, it will focus on using **Visual Studio** on a windows PC (as opposed to VS Code with extentions on a mac since Visual Studio Mac was discontinued late 2024). My references will be left at the bottom of the document. The vast majority of my notes for C# will come from the Microsoft official documentation and a Udemy course I'm following offered by Denis Panjuta.

<br>

---

## Quick Tips
- In VS Code You can press `ctrl` + `shift` + `p` on Windows or `cmd` + `shift` + `p` on Mac, to open the command palette. In Visual Studio there's a similar feature called Quick launch which can be opened with the same hotkeys or simply `ctrl` + `Q`.

- You can use `ctrl` + `K` followed by `ctrl` + `D` to format the entire document, adding indents and spaces where needed. Alternatively, you can use the quick launch to find this and similar commands.

<br>
<br>

---

## **Fundamentals**

C# is the primary language of the .NET platform, a free, open-source, cross-platform development environment used to build applications for devices ranging from IoT to cloud services. It is a general-purpose, object-oriented language influenced by C, C++, and Java, designed for developer productivity and high performance while supporting functional techniques and low-level efficiency without unsafe code. With millions of users and strong ecosystem support across all .NET workloads, C# powers most of the .NET runtime and libraries, making it familiar, versatile, and widely adopted for modern app development.

<br>
<br>

### C# Versions
Here are some notable changes in c# versions that have shaped the language and brought it to the modern world.

C#3(2007)
- LINQ (Language Integrated Query): Unified querying for collections, objects, XML, and SQL—all with a declarative, SQL-like syntax directly in C#.
- Implicit Typing (var): Cleaner code with type inference for locals.

C#5(2012)
async/await Syntax: Brought first-class support for asnchronous programming, dramatically simplifying code that would otherwise be callback-heavy or complex.

C#6-7(2015-2018)
- Deconstruction: Allows extracting values fro man objext or tuple and assign it to a variable.
- Index/Ranges (^1, ..): Elegant list slicing and reverse-indexing like Python and Javascript.
- String interoplation: Adds a `$` syntax prefixing a string to denote a string that allows variables/code.

C#8(2019)
Nullable Reference Types: Brought null-safety, closing one of C#'s biggest historic gaps compared to F# or Kotlin.'

C#9-C#10(2020-2012)
- Record Types: Immutable data objects for DDD and modern functional approaches.
- Init-Only Properties: Helped with immutable structures and safe creation patterns.
- Global Usings and File-Scoped Namespaces: Reduced clutter and standardized code style at scale.

C#12(2023)
- Collections expressions:
  - Initialize lists and arrays using bracket syntax. `List<int> nums = [1, 2, 3]; // Instead of new List<int> { 1, 2, 3 }`
  - Spread operator `..` to merge collections.
  ```
  int[] a = [1, 2, 3];
  int[] b = [4, 5];
  int[] joined = [..a, ..b, 6, 7]; // Merges and appends[4][2][8]
  ```
- Primary Constructors: Specify constructor parameters directly in the class/struct header, reducing boilerplate.
``` class Point(int x, int y)
{
  // use x and y directly
}
```

LINQ, async/await, records, pattern matching, range/index operators, and collection expressions are the landmark features that steadily modernized C#, making it both expressive and competitive with dynamic languages like JS, Python, and Kotlin. Each provided a leap in ergonomics, safety, or performance—just as ES6 did for JavaScript.

<br>
<br>

### Naming Convention
In C# the naming convention for variables is `camelCase` starting with a lowercase letter then delimiting words by an uppercase. This applied to variables and method parameters. Most other things such as file names, class names, methods and properties are `PascalCase` or UpperCamelCase starting with a capital letter. Also, variables <mark> cannot start with a number</mark> but can start with an underscore.

<br>

### Strings
...

<br>

#### String Literal
...

<br>

#### Concatenation
...

<br>

#### Interpolation
...

<br>

#### Verbatim Syntax and MultiLine Strings
...

<br>
<br>

### Numbers and Math
...Mentioned checked() which will output an error instead of a random number
... Mention casting (int)42.1
Mention 32bit arithmetics and 64bit arithmetics
float and double are binary floating-point types so when doing math the float is converted to double. decimal is decimal floating point so cannot do math with float and double.

<br>

#### Int
...

<br>

#### Long
...

<br>

#### Float
...

<br>

#### Double
...

<br>

#### Decimal
...

<br>
<br>

#### Var
...

<br>

### List<T> (List of T)
...`List<string> friends = new List<string>` | `var friends = new List<string>`
flexible, used for most operations.

<br>

### Arrays
...Fixed, used for precision or performance, like when you know the amount won't change.
Can add with 

<br>

### Working with Lists/Arrays
...

<br>

#### Accessing index
[0]
[^1]
[2..4] e.g. foreach (string name in names[2..4])

<br>

#### Add
...

<br>

#### Remove
...

<br>

#### Clear
...

<br>

#### Contains
...

<br>

#### Sort
...

<br>

#### IndexOf
...

<br>

### Conditionals and Loops
... mention indentation(4 space/1 tab) and how brackets are on a new line.
no braces means one line only, curly braces as long as u want.

<br>

#### If Statement
...

<br>

#### Comparison Operators
...For value types (like int, structs), == compares the actual values.

For reference types, by default == compares references (whether two variables refer to the exact same object).

Some reference types, such as string, override == to compare values (content) instead of references, making string comparisons intuitive.

&& || | . + - * / == > < >= <= ++ --

short circuiting

<br>

#### While
...

<br>

#### Do While
...

<br>

#### For Loops
...

<br>

#### For Each
...

<br>

### LINQ (Language Integrated Query)
Differs from other langauges like JavaScript where you create a string from another language like `SQL` e.g. `Select * from games` which is not integrated and is not checked for mistakes. It is built to be used somewhere else. LINQ on the other hand is integrated into the language and has words like `from`, `select`, `where`, `in`, etc. The compiler can evaluate this **query syntax** for mistakes. It is not `SQL`, it is a language integrated query.

```C#
// Data
List<int> grades = [21, 42, 63, 84, 99];

// Deferred execution means it is not executed immediately when it is defined but only when you enumerate over it.
// The "Question", not yet executed (deferred execution). Query Expression.
IEnumerable<int> highGrades =
  from grade in grades // required
  where grade >= 80 // optional
  orderby grade descending // optional
  select grade; // must end in select or group.

// The "Answer", executing the query.
foreach (int grade in highGrades)
{
  Console.WriteLine($"{grade}, congrats!");
}
```

<br>

#### 
...

<br>

---

## **Resources**

<br>
<br>

#### **References**

[Microsoft's Official C# Language Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/)

[Complete C# Masterclass by Denis Panjuta](https://www.udemy.com/course/complete-csharp-masterclass/)

[C# Cheat Sheet by Zero to Mastery (ZTM)](https://zerotomastery.io/cheatsheets/csharp-cheat-sheet/)

[Perplexity AI](https://www.perplexity.ai/)

<br>
<br>

#### **Tools**

-   C# Playground &rarr; [Net Fiddle](https://dotnetfiddle.net/)

<br>
<br>

---
