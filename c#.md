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

<br>
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

---

## **Resources**

<br>
<br>

#### **References**

[Microsoft's Official C# Language Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/)

[Complete C# Masterclass by Denis Panjuta](https://www.udemy.com/course/complete-csharp-masterclass/)

[C# Cheat Sheet by Zero to Mastery (ZTM)](https://zerotomastery.io/cheatsheets/csharp-cheat-sheet/)

<br>
<br>

#### **Tools**

-   C# Playground &rarr; [Net Fiddle](https://dotnetfiddle.net/)

<br>
<br>

---
