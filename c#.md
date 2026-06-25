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
- C# is a truly object-oriented programming language meaning technically everything inherits from the `object` class.
- C# uses 4 tab spaces instead of 2. Both are allowed but 4 is the convention.
- C# uses semicolons `;` to denote the end of a line. This usually isn't necessary when closing code blocks `{}`. This is common for the C family of languages.
- In VS Code You can press `ctrl` + `shift` + `p` on Windows or `cmd` + `shift` + `p` on Mac, to open the command palette. In Visual Studio there's a similar feature called Quick launch which can be opened with the same hotkeys or simply `ctrl` + `Q`.
- You can use `ctrl` + `K` followed by `ctrl` + `D` to format the entire document, adding indents and spaces where needed. Alternatively, you can use the quick launch to find this and similar commands.
- number types (`int`, `short`, `long`), floating types (`float`, `double`, `decimal`), logical type (`bool`), and character type (`char`) are value types.
- `string`, `dynamic`, `class`, `array`, `interface`, `record`, and `object` types are **reference types**.

<br>
<br>

---

## **Fundamentals**

C# is the primary language of the .NET platform, a free, open-source, cross-platform development environment used to build applications for devices ranging from IoT to cloud services. It is a general-purpose, object-oriented language influenced by C, C++, and Java, designed for developer productivity and high performance while supporting functional techniques and low-level efficiency without unsafe code. With millions of users and strong ecosystem support across all .NET workloads, C# powers most of the .NET runtime and libraries, making it familiar, versatile, and widely adopted for modern app development.

<br>

### C# Versions
Here are some notable changes in C# versions that have shaped the language and brought it to the modern world.

#### C#3 (2007)
- LINQ (Language Integrated Query): Unified querying for collections, objects, XML, and SQL—all with a declarative, SQL-like syntax directly in C#.
- Implicit Typing (var): Cleaner code with type inference for locals.

<br>

#### C#5 (2012)
async/await Syntax: Brought first-class support for asnchronous programming, dramatically simplifying code that would otherwise be callback-heavy or complex.

<br>

#### C#6-7 (2015-2018)
- Deconstruction: Allows extracting values fro man objext or tuple and assign it to a variable.
- Index/Ranges (^1, ..): Elegant list slicing and reverse-indexing like Python and Javascript.
- String interoplation: Adds a `$` syntax prefixing a string to denote a string that allows variables/code.

<br>

#### C#8 (2019)
Nullable Reference Types: Brought null-safety, closing one of C#'s biggest historic gaps compared to F# or Kotlin.'

<br>

#### C#9-C#10 (2020-2012)
- Record Types: Immutable data objects for DDD and modern functional approaches.
- Init-Only Properties: Helped with immutable structures and safe creation patterns.
- Global Usings and File-Scoped Namespaces: Reduced clutter and standardized code style at scale.

<br>

#### C#12 (2023)
- Collections expressions:
  - Initialize lists and arrays using bracket syntax. `List<int> nums = [1, 2, 3];` Instead of `new List<int> { 1, 2, 3 };`
  - Spread operator `..` to merge collections.
  ```C#
  int[] a = [1, 2, 3];
  int[] b = [4, 5];
  int[] joined = [..a, ..b, 6, 7]; // Merges and appends[4][2][8]
  ```
- Primary Constructors: Specify constructor parameters directly in the class/struct header, reducing boilerplate.
```C#
class Point(int x, int y)
{
    // use x and y directly
}
```

<br>

#### C#14 (2025)
- Extension Members:
  - Extends extension methods to support properties, operators, and static members.
  - One of the largest evolutions of C#'s extensibility model since extension methods themselves

LINQ, async/await, records, pattern matching, range/index operators, and collection expressions are the landmark features that steadily modernized C#, making it both expressive and competitive with dynamic languages like JS, Python, and Kotlin. Each provided a leap in ergonomics, safety, or performance—just as ES6 did for JavaScript.

<br>

### Operators
#### Arithmetic Operators
|Symbol|Name|Description|
|:------:|----|-----------|
|`+`|Addition|Adds two operands.|
|`-`|Subtraction|Subtracts right from left operand.|
|`*`|Multiplication|Multiplies operands.|
|`.`|Division|Divides left by right operand.|
|`%`|Modulus|Remainder of division.|
|`++`|Increment|Increases value by 1.|
|`--`|Decrement|Cecreases value by 1.|

<br>

#### Assignment Operators
|Symbol|Name|Description|
|:------:|----|-----------|
|`=`|Assignment|Assigns right to left.|
|`+=`|Add assignment|Adds and assigns.|
|`-=`|Subtract assignment|Subtracts and assigns.|
|`*=`|Multiply assignment|Multiplies and assigns.|
|`/=`|Divide assignment|Divides and assigns.|
|`%=`|Modulus assignment|Applies modulus and assigns.|
|`&=`|AND assignment|Bitwise AND and assigns.|
|`\|=`|OR assignment|Bitwise OR and assigns.|
|`^=`|XOR assignment|Bitwise XOR and assigns.|
|`<<=`|Left shift assignment|Shifts and assigns.|
|`>>=`|Right shift assignment|Shifts and assigns.|
|`??=`|Null-coalescing assignment|Assigns if left is null.|

<br>

#### Comparison/Relational Operators
|Symbol|Name|Description|
|:------:|----|-----------|
|`==`|Equality|True if left equals right.|
|`!=`|Inequality|True if not equal.|
|`<`|Less than|True if left is less than right.|
|`<=`|Less than or equal|True if left is less than or equal to right.|
|`>`|Greater than|True if left is greater than right.|
|`>=`|Greater than or equal|True if left is greater than or equal to right.|

<br>

#### Logical Operators
|Symbol|Name|Description|
|:------:|----|-----------|
|`&&`|AND|True if both are true.|
|`\|\|`|OR|True if either is true.|
|`!`|NOT|True if operand is false.|

<br>

#### Bitwise and Shift Operators
|Symbol|Name|Description|
|:------:|----|-----------|
|`&`|Bitwise AND|Bitwise AND for integer types.|
|`\|`|Bitwise OR|Bitwise OR for integer types.|
|`^`|Bitwise XOR|Bitwise XOR for integer types.|
|`~`|Bitwise NOT|Bitwise complement.|
|`<<`|Bitwise Left shift|Shifts bits to the left.|
|`>>`|Bitwise Right shift|Shifts bits to the right.|

<br>

#### Other Operators
|Symbol|Name|Description|
|:------:|----|-----------|
|`.`|Member access|Access member of a type or namespace.|
|`?:`|Conditional (ternary)|Ternary conditional operator.|
|`??`|Null-coalescing|Returns lefti f not null; otherwise, right.|
|`?.`|Null-conditional|Calls or accesses right if left is not null.|
|`[]`|Array/indexer access|Accesses element.|
|`()`|Method call/grouping|Calls method or groups an expression|
|`_>`|Pointer member access|Accesses member via pointer.|
|`*`|Pointer deference|Dereferences a pointer.|
|`&`|Address-of (_pointer_)|Returns address of variable.|
|`sizeof`|Size of type|Gets size in bytes.|
|`typeof`|Returns System.Type|Gets type object.|
|`is`|Type compatibility|True if compatible types.|
|`as`|Type conversaion|Converts or null|
|`new`|Instantiation|Creates an object or array.|
|`delegate`|Anonymous method|Used to declare delegate type instance.|
|`checked`|Explicit overflow check|Check arithmetic for overflow.|
|`unchecked`|Suppress overflow check|No overflow check.|
|`default`|Default value assignment|Assigns default value for type.|
|`nameof`|Result is string name|Gets string of variable/type/member name/|

<br>
<br>

### Variables and Naming Conventions
C#, like most other programming languages, uses variables to store and access data. In C# the naming convention for variables is **camelCase** starting with a lowercase letter then delimiting words by an uppercase. This applied to variables and method parameters. Most other things such as file names, class names, methods and properties are **PascalCase** or UpperCamelCase starting with a capital letter. Also, variables <mark style="background-color: #c48ac1">&nbsp; cannot start with a number&nbsp;</mark> but can start with an underscore.

C# is a statically typed langauge that requires you to explicitly declares the type of every variable, except when using the `var` keyword. With `var`, the compiler infers the variable's type based on the assigned value at compile time.

```C#
// Explicitly declared as string.
string aStringVariable = "some string";

// Explicitly declared as int.
int aNumber = 1;

// inferred as string
var anotherStringVariable = "Some other string";

// inferred as int
var anotherNumber = 2;
```

<br>

### Constants
Constants are immutable variables that cannot be changed. They typically follow the **PascalCase** naming convention beginning with an uppercase letter.

```C#
const int YearOfBirth = 1996;
```

<br>

### Comments
Single line comments are denoted by prepending the code with two forward slashes `//`. Multi-line comments are denoted by typing your code between the opening `/*` and closing `*/`.

```C#
// This is a single line comment.

// .NET Coding Conventions actually recommends
// using single line comment syntax
// for multiple lines e.g. code explanations.

/* This is an inline style for multi-line comments. */

/*
This is "commented out"
style for quickly
commenting out a code block */

/*
This is also a multi-line
but should only be used at
the top of files as a legal/copyright header
*/

/* Starred block style approach
  * recommended for descriptions.
  * Clean and easy to read.
  * Typically at the top of the file.
  */
```

<br>

### Strings
A string in C# is a series of characters between double quotes `"string"`. This can be a [string literal](#string-literal) or perhaps a value returned in the form of a string.

```C#
// Reads input from the user, stored as a string.
string userResponse = Console.ReadLine();
```

<br>

#### String Literal
A string literal is when we *literally* describe the exact string we want.

```C#
string name = "This is a string literal";
```

<br>

#### Raw String Literals
A raw string literal is useful for creating multi-line strings and for providing a syntax that doesn't require escaping characters a normal **string literal** would (e.g. `"escape \"backslash\""` **&rarr;** `escape "backslash"`). It starts and ends with **at least three** double quotes (`"""`), if you want to add three double quotes **inside** the string then add extra double quotes to the start and end of the string.
If the raw string literal is on one line, the double quotes(`"""`) need to be one the same line. If it spans multiple lines then the double quotes must be on their own line. You can read more on &rarr; [Microsoft's official Learn C# Guide | Raw string literals](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/strings/#raw-string-literals).

**Some useful exmaples from Microsoft's Guide:**
```C#
// ✅ Valid: Single line raw string literal requires double quotes on the same line.
string singleLine = """Friends say "hello" as they pass by.""";


// ✅ Valid: Multi-line raw string literal requires double quotes on their own line.
string multiLine = """
    "Hello World!" is typically the first program someone writes.
    """;


// ✅ Valid
string embeddedXML = """
    <element attr = "content">
        <body style="normal">
            Here is the main text
        </body>
        <footer>
            Excerpts from "An amazing story"
        </footer>
    </element >
    """;


// ❌ Invalid: Characters appear on the same line as the opening quotes.
var multiLineStart = """This
    is the beginning of a string 
    """;


// ❌ Invalid: Characters appear on the same line as the closing quotes.
var multiLineEnd = """
    This is the beginning of a string """;


// ❌ Invalid: Text cannot be outdented further than the closing tag.
var noOutdenting = """
        A line of text, this is allowed.
    Trying to outdent the second line, this is not allowed.
        """;
```

<br>

#### Concatenation
String concatenation is the act of adding multiple strings together to form one bigger string.

```C#
string firstName = "Santa";
string lastName = "Clause";
string fullName = firstName + " " + lastName;
Console.Write(fullName); // Outputs "Santa Clause"
```

<br>

#### Interpolation
String interpolation is when we want to mix code/variables within a string, with the output being a string. Many times this will more readable and concise than concatentation. It is denoted by a `$` symbol preceding the string. To allow the use of code/variables, you use `{}` curly/squiggly braces and write the code inside. The compiler will resolve and replace the code with the value.

```C#
string firstName = "Santa";
string lastName = "Clause";
string fullName = $"{firstName} {lastName}";
Console.Write(fullName); // Outputs "Santa Clause"
```

<br>

#### Verbatim Syntax and MultiLine Strings
Varbatim syntax is when we want the string to appear exactly as we've typed it. This may sound like a string literal, but the differences is that in normal strings, we can use certain special syntax such as  `\n` to create a new line. Because of this, sometimes we must use a backslash `\` followed by another character to perform some sort of action. The `\` however is invalid by itself in a string since the compiler is expecting special syntax. Therefor, it must be _escaped_ by another `\` like so `\\`. That would output a single `\`. Also, we can't naturally span a string over several lines without the use of `\n`. So, if we want the string to appear exactly as we typed it, including new lines and all special characters (_removing the ability to use special syntax like `\n`_), we need to prepend the string with the `@` symbol. This can be mixed with the `$` symbol for interoplation and can be before or after the `$`. E.g. `@$` or `$@` are valid.

```C#
// Regular string literal.
string example1 = "I       am a string \n Now I am the same string on a new line. \\ <-- this backslash must be escaped or it will raise an error."
+ "\nThis is concatenated and starts with a new line!";

/* Output:
"I       am a string
Now I am the same string on a new line. \ <-- this backslash must be escaped or it will raise an error.
This is concatenated and starts with a new line!"
*/


// Verbatim Syntax
int randomNumber = 123;
string example2 = @$"I       am a string 
Now I am the same string on a new line. \ <--- this backslash is perfectly fine.
This is an interpolated variable on a new line, randomNumber = {randomNumber}!";

/* Output
I       am a string
Now I am the same string on a new line. \ <--- this backslash is perfectly fine.
This is an interpolated variable on a new line, randomNumber = 123!
*/
```

#### Handy String Methods
Here are a few string methods that are often used.

```c#
// Example strings
string bookExcerptPart1 = "In the shade of the house, in the sunshine on the river bank by the boats. ";
string bookExcerptPart2 = "In the shade of the sallow wood and the fig tree.";
string name = "Denzel Braithwaite";


// 💡ToUpper() - Converts the string to uppercase.
string loudBookExcerpt = bookExcerptPart1.ToUpper(); // IN THE SHADE OF THE HOUSE, IN THE SUNSHINE ON THE RIVER BANK BY THE BOATS.


// 💡ToLower() - Converts the string to lowercase.
string quietBookExcerpt = bookExcerptPart1.ToLower(); // in the shade of the house, in the sunshine on the river bank by the boats.


// 💡PadLeft() and PadRight() - Pads the string with spaces or specified characters to a certain length.
// The int you pass as an argument is the desired length of the string, not the amount of padding to add.
string paddedName = name.PadLeft(23); // the {name} variable has 18 chars, so 5 spaces were added to the start of the string to reach the desired 23 chars.
paddedName = paddedName.PadRight(28); // the {name} variable has 23 chars, so 5 spaces were added to the end of the string to reach the desired 28 chars.
Console.WriteLine($"[{paddedName}]"); // Outputs [     Denzel Braithwaite     ]
string anotherPadExample = name.PadRight(20, '-'); // the {name} variable has 18 chars, so 2 dashes (-) were added to the end of the string to reach the desired 20 chars.
Console.WriteLine($"[{anotherPadExample}]"); // Outputs [Denzel Braithwaite--]
anotherPadExample = anotherPadExample.PadRight(10, '!'); // the {anotherPadExample} variable has 20 chars, so nothing was added to the end of the string since it is already over 10 chars.


// 💡Concat() - Joins two or more strings. The compiler converts the `+` operator to Concat() behind the scenes. Same as bookExcerptPart1 + bookExcerptPart2;
string fullBookExcerpt = String.Concat(bookExcerptPart1, bookExcerptPart2);


// 💡Split() - Splits the string into substrings based on a delimiter.
string[] rippedBook = fullBookExcerpt.Split(' '); // ["In", "the", "shade", "of", "the", "house", "in", "the", "sunshine", "on", "the", "river", "bank", "by", "the", "boats.", "..."] etc.


// 💡Join() - Converts arrays/lists/collections into a string via a separator, even if the array is mixed or doesn't contain strings.
string repairedBook = String.Join(' ', rippedBook); // In the shade of the house, in the sunshine on the river bank by the boats. In the shade of the sallow wood and the fig tree.
string repairedBookCopy = string.Join(' ', rippedBook); // Same thing, (s)tring is an alias for (S)tring.


// 💡IndexOf() - Finds the index of the first occurrence of a character or substring.
int startIndex = bookExcerptPart1.IndexOf("in the sunshine on the river bank"); // 27


// 💡LastIndexOf() - Finds the index of the last occurrence of a character or substring.
int lastIndex = fullBookExcerpt.LastIndexOf("the"); // 111


// 💡Substring() - Returns a portion (substring) of the string, if no end index is specified it will return the rest of the string from the start index.
string bestPart = bookExcerptPart1.Substring(startIndex); // in the sunshine on the river bank by the boats.
string worstPart = fullBookExcerpt.Substring(lastIndex); // the fig tree.


// 💡Compare() - Compares two strings to determine which comes first in lexical/alphabetical order. Returns either -1, 0, or 1.
string fruitA = "Apple";
string fruitB = "Banana";
Console.WriteLine(String.Compare(fruitA, fruitB)); // Outputs -1 since "Apple" comes before "Banana"
// Modern approach to ensure case-insensitive comparison
Console.WriteLine(String.Compare(fruitA, "apple", StringComparison.OrdinalIgnoreCase)); // Outputs 0 since it is ignoring casing so "Apple" == "apple".


// 💡Replace() - Replaces specified characters or substrings with new ones. Arguments must be 2 strings or 2 chars, cannot be 1 string and 1 char.
string improvedBookExcerpt = bookExcerptPart2.Replace("fig tree", "orange"); // In the shade of the sallow wood and the orange.


// 💡Contains() - Checks if the string contains a specified substring.
bool gotAnyOranges = improvedBookExcerpt.Contains("orange"); // True
// Many string methods support `StringComparison` for case-insensitive checks.
gotAnyOranges = improvedBookExcerpt.Contains("Orange", StringComparison.OrdinalIgnoreCase); // True since now case-insensitive


// 💡Trim() - Removes leading and trailing whitespace.
string paddedNameTrimmed = paddedName.Trim(); // [Denzel Braithwaite] (brackets added to visualize whitespace)


// 💡TrimStart() - Removes leading whitespace.
string paddedNameTrimmedStart = paddedName.TrimStart(); // [Denzel Braithwaite     ] (brackets added to visualize whitespace)


// 💡TrimEnd() - Removes trailing whitespace.
string paddedNameTrimmedEnd = paddedName.TrimEnd(); // [     Denzel Braithwaite] (brackets added to visualize whitespace)


// 💡StartsWith() - Checks if the string starts with a specific substring.
bool didBookStartWithFigTree = fullBookExcerpt.StartsWith("fig tree."); // False


// 💡EndsWith() - Checks if the string ends with a specific substring.
bool didBookEndWithFigTree = fullBookExcerpt.EndsWith("fig tree."); // True


// 💡Remove() - Removes characters from a string starting at a specified index. Will crash if not found since index will be -1.
string stolenLastPage = fullBookExcerpt.Remove(fullBookExcerpt.IndexOf(bookExcerptPart2)); // In the shade of the house, in the sunshine on the river bank by the boats. 
// Safer approach in case the substring is not found.
int index = fullBookExcerpt.IndexOf(bookExcerptPart2);
stolenLastPage = index >= 0 ? fullBookExcerpt.Remove(index) : fullBookExcerpt;
Console.WriteLine(stolenLastPage);


// 💡Insert() - Inserts a substring at a specified index.
string newFirstPage = bookExcerptPart1.Insert(0, "In a village far away at a time long ago. "); // In a village far away at a time long ago. In the shade of the house, in the sunshine on the river bank by the boats. 


// 💡ToCharArray() - Converts the string to a char array.
char[] cutUpPage = newFirstPage.ToCharArray(); // ['I', 'n', ' ', 'a', ' ', 'v', 'i', 'l', 'l', 'a', 'g', 'e', '.'] etc.
```

<br>
<br>

### Chars
It's important to remember that `char` and `string` do not mix. A `char` is a single character, whereas a `string` is a **sequence of characters**, even if it has length 1.

```C#
// Denoted with single quotes.
char c = 'a';

// Denoted with double quotes.
string s = "a";

// ❌ This is an error: you can't compare char to string directly.
c == s;

// ✅ This works: s[0] will return the char at that index.
c == s[0];
```

Another example of a pitfall:

```C#
// sentence is a string, nothing fancy here.
string sentence = "Howdy do partner?";


// Count iterates over each CHAR in the sentence string, therefore `c` must be compared with another char.
int count = sentence.Count(c => c == 'a'); // ✅ Comparing char with char.
int badCount = sentence.Count(c => c == "a"); // ❌ Can't compare char with string.
```

So if this happens, an easy solution is to convert the `string` to a `char`.

```C#
foreach (string letter in alphabet)
{
    char c = letter[0]; // Effectively converts the string to a char since letter is a string of length 1.
    int amount = sentence.Count(l => l == c); // Now we can compare a char with a char.
    Console.WriteLine($"{letter}: {amount}"); // Example output: E: 3
}
```

<br>
<br>

### Numbers and Math
There are quite a few number types in C#, so we will focus on the most common. Typically, you will either have a whole number (`42`), or a number with decimal point (`42.1`). Number types have limits, meaning not all of them can handle the same numbers. Some are designed to hold very large numbers while others can only hold numbers up to **255**. This relates to how much memory is used to store the number.

For simple numbers that are whole and not expected to exceed `2,147,483,648 to 2,147,483,647`, the most common choise is the `int` type. For bigger numbers, it's common to use `long` instead, which has a limit of `9,223,372,036,854,775,807` (_e.g. counting populations or file bytes_).

```C#
// int makes sense here since age will never exceed the maximum number.
int age = 29;

// The compiler will naturally assign this the int type if not explicity.
var anotherAge = 29;

// Way too big to store in an int.
long videoViews = 812334333685478;

// Compiler can't fit this into an int, so will use a long.
var video2Views = 628934231635499;
```

<br>

For numbers that use decimal points, there are three common choices depending on your scenario.
- float - Uses the `f` suffix. When Precision isn't important but performance is. Useful when memory is restricted.
- double - Optionally Uses the `d` suffix. When you want balance between precision and performance. This is generally recommended as the default type for most numbers with decimal points (_floating-point numbers). The compilor defaults to double, it is twice as precise as float and good for math.
- decimal - Uses the `m` suffix. When precision is essential (_accounting, money_).

<mark style="background-color: #c48ac1">&nbsp;When performing arithmetic operations, `floats` and `doubles` cannot be mixed with `decimals`&nbsp;</mark>
(more about that [_here_](#arithmetics-with-floats-doubles-and-decimals)).

<br>

```C#
// float syntax, the 'f' is mandatory.
float floatingNumber = 10.1f; // Outputs 10.1
float floatingNumber2 = 10.1F; // Outputs 10.1

// double syntax, the 'd' is optional.
double doubleNumber = 10.1; // Outputs 10.1
double doubleNumber2 = 10.1d; // Outputs 10.1
double doubleNumber3 = 10.1D; // Outputs 10.1

// decimal syntax, the 'm' is mandatory.
decimal decimalNumber = 10.1m; // Outputs 10.1
decimal decimalNumber2 = 10.1M; // Outputs 10.1
```

<br>

**Note:** If you attempt to store a floating-point number inside a type such as float but forget the `f` suffix, the compiler will default to `double` and then attempt to put that `double` into the type you explicitly stated, which will raise a compile-time error unless you used `var` or `double` as the type.

```C#
// ✅ Valid: Compiler sees float, user wants to store as float, all is good.
float floatingNumber1 = 10.1f;

// ❌ Invalid: Compiler defaults to double, user wants float, doesn't work.
float floatingNumber2 = 10.1;

// ✅ Valid: Compiler sees float, user let's compiler decide type, it becomes a float.
var floatingNumber3 = 10.1f;

// ✅ Valid: Compiler defaults to double, user let's compiler decide, it becomes double.
var floatingNumber3 = 10.1;
```

<br>

#### Arithmetics with floats, doubles and decimals.
`float`, `double` and `decimal` numbers have different memory sizes.

- float - Uses 32 bits to store a number as a binary floating-point value, offering about 7 digits of percision.
- double - Uses 64 bits to store a number as a binary floating-point value, offering 15-16 digits of precision.
- decimal Uses 128 bits and is store in base 10 (_not binary_) which avoids typical rounding errors seen with binary floating-point types.

<br>

Because of this, when performing arithmetics, it is impossible for these types to be mixed, since they handle arithmetics different. They use a different _calculator_ so to speak, where `float` and `double` use a binary (0-1) based calculator, `decimal` uses a decimal (0-9) based calculator.

|Operand Type|Works Implicitly?|Requires Explicit Conversion?|Explanation|
|:----------:|:---------------:|:---------------------------:|-----------|
|float + float|Yes|No|Both are same type, implicit arithmetic works.|
|float + double|Yes (to double)|No|float implicitly converts to double; result is double.|
|float + decimal|No|Yes|decimal does not implicitly convert to/from float; explicit cast needed.|
|double + double|Yes|No|Both are same type, implicit arithmetic works.|
|double + decimal|No|Yes|decimal and double are incompatible; explicit conversion required.
|decimal + decimal|Yes|No|Both are same type, implicit arithmetic works.

<br>

#### Checked Keyword
The `checked` keyword enforces overflow checking. In a **checked context**, if an operation exceeds the storage capacity of the target type (_e.g. adding beyond `int.MaxValue`_), a `System.OverflowException` is thrown. In aun **unchecked context** (_the default for most builds_), overflow causes silent truncation or wraparound rather than exception (_meaning you won't get an error but your value will be inaccurate_). `checked` affects operations textually inside its scope, meaning only those operations written inside the `checked { }` block or expression use overflow checking.

```C#
int c = int.MaxValue;
int d = a + 1; // Silently stores an incorrect value

checked
{
    int a = int.MaxValue;
    int b = a + 1; // Throws OverflowException
}
```

In essence, `checked` helps catch overflow errots in intergral math and conversions.

<br>

#### Casting
Casting between numeric types explicitly attempts to convert one type to another. This can be useful when performing arithmetic operations on floating-points that cannot be implicitly converted such as `float` and a `decimal` (Refer to the above [table](#arithmetics-with-floats-doubles-and-decimals)).

```C#
float floatingNumber = 1.23f;
decimal decimalNumber = 1.23m;

// ❌ Error, cannot use `+` with float and decimal.
var newFloatingNumber1 = floatingNumber + decimalNumber;

// ✅ Outputs 2.46. Explicitly converts float to decimal. decimal + decimal is valid.
var newFloatingNumber2 = (decimal)floatingNumber + decimalNumber;
```

<br>
<br>

### Dynamic Type
The `dynamic` type indicates that the variable and references to its members bypass compile-time type checking. It behaves like type `object` in most circumstances. <mark style="background-color: #c48ac1">&nbsp;Any non-null expression can be converted to the dynamic type.&nbsp;</mark> Type `dynamic` differs from type `object` in that the compiler doesn't resolve or type check operations that contain dynamic expressions. The dynamic type only exists at compile time, not run time; dynamic variables are compiled into variables of type `object`. Read more here &rarr; [Microsoft's official Learn C# Guide | The dynamic type](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/reference-types#the-dynamic-type).

> **Note:** In C# all primitive value types can be treated as objects since they all inherit from the `System.Object` class. The difference between `var` and `dynamic` is that `var` lets the compiler look at the value on the right-side of the `=` operator (_called implicit typing_) and assign the type based on that at compile-time, whereas `dynamic` tells the compiler ignore this at compile-time and treat this as an object which can be anything during runtime.

<br>
<br>

### Tuples
Tuples are an ordered sequence of values with a fixed length. Each element of a tuple has a type and an optional name. Since tuples types are structural types, they don't need names like `string` or `int`. Tuple names should be **PascalCase**. A tuple type is defined by the number of members (_referred to as arity_), and the types of those members. Read more here &rarr; [Microsoft's official Learn C# Guide | Tuples](https://learn.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/tutorials/tuples-and-types#tuples).

> **Note:** In C#, _arity_ refers to the number of arguments, parameters, or type elements that a specific code construct accepts. You can assign a tuple to <mark style="background-color: #c48ac1">&nbsp;a tuple with the same arity and types&nbsp;</mark> even if the members have different names.

<br>

**Syntax**
```C#
// With names
var someBook = (page1: "The quick brown fox", page2: "jumped over the lazy dog");

// Without names with mixed types
var noNameMixedTuple = ("Luigi", 2, true);
```

<br>

You can also create new _tuples_ from existing ones using the `with` expression so long as the structure matches. What's important to remember is <mark style="background-color: #c48ac1">&nbsp;the names do not matter, only the type and amount of members.&nbsp;</mark>

```C#
// ✅ First we define a tuple
var someBook = (page1: "The quick brown fox", page2: "jumped over the lazy god"); // Value: ("The quick brown fox", "jumped over the lazy god");


// ✅ Then we create a new tuple using `with` and modify page2.
var someBookReprinted = someBook with {page2 = "jumped over the lazy dog"}; // Value: ("The quick brown fox", "jumped over the lazy dog");


// ❌ But here we try to add a new page that never existed, resulting in an error.
// This is a problem because now we have page1, page2 and "page3"?
var illegalModifiedCopyOfSomeBook = someBook with {page2 = "jumped over the lazy dog", page3 = "and the dog got angry"};


// The issue with the line above is that it changes the STRUCTURE which cannot be implicitly converted.
// ✅ Changing the names is valid since the amount of members and their types have not changed.
var aBlankBook = (pageA: "", pageB: "");
aBlankBook = someBook; // Value: ("The quick brown fox", "jumped over the lazy god");

// ❌ Here we try to change the type of the page from string to int which cannot be implicitly converted.
var aBookAboutNumbers = someBook with {page1 = 123};
```

Notice how the `Console.WriteLine(someBook)` doesn't care about the names, it prints: `("The quick brown fox", "jumped over the lazy god")`. <mark style="background-color: #c48ac1">&nbsp;The names are just compile-time syntactic sugar.&nbsp;</mark> Names or not, you can still access or modify tuple members with ease.

```C#
var marioBrothers = (olderBro: "Mario", youngerBro: "Luigi");

// Modify
marioBrothers.olderBro = "Toad";
marioBrothers.Item2 = "Peach";

// Access
Console.WriteLine(marioBrothers.youngerBro); // Outputs Peach
Console.WriteLine(marioBrothers.Item1); // Outputs Toad
```

<br>
<br>

### Record Type
A record is a specialized type of _class_ or _struct_ <mark style="background-color: #c48ac1">&nbsp;designed to represent data rather than behaviour.&nbsp;</mark> Think of a record as a shipping label; if we print multiple shipping labels with the exact same information, they are essentially the same since all we care about is the information. This differs from typical class instances where <mark style="background-color: #c48ac1">&nbsp;the identity and behaviour is important.&nbsp;</mark> Imagine twins that are identical in every way, they are still unique people that **should not be used interchangeably** since they are in fact different.

> **Note:** In C#, top-level statements must precede namespace and type declarations. This differs from other languages such as **JavaScript** which allows you to freely mix executable code (_e.g. `Console.log()`_), function declarations, and class definitions anywhere in a file. JavaScript _hoists_ function declarations to the top of their scope so you can call a function before it is defined. <mark style="background-color: #c48ac1">&nbsp;C# is strict and requires execution code to be at the very top of the file while _namespaces_, classes, structs, and _interfaces_ close the top-level statement section. **You cannot place any executable code below a type declaration!**&nbsp;</mark>

<br>

**Record Syntax**
```C#
var animal1 = new Animal("dog", "black");
var animal2 = new Animal("dog", "black");
Console.WriteLine(animal1 == animal2); // True, value is compared not reference

// Remember this has to be at the bottom.
public record Animal(string Species, string Color);
```

<br>

**Compared to Classes**
```C#
var animal1 = new Animal("dog", "black");
var animal2 = new Animal("dog", "black");
Console.WriteLine(animal1 == animal2); // False, compares object identity by default

// Remember this has to be at the bottom.
public class Animal (string Species, string Color)
{
    // Properties
    public string Species { get; set; } = Species;
    public string Color { get; set; } = Color;
}
```

The records are still 2 different objects in memory but their equality is based on their value not their reference. Reference equality asks: "**Are these the exact same object?**" Value equality asks: "**Do these objects contain the same data?**". Records generate value-based equality members (_including `==`_) by default. This causes two record instances with the same data to be considered equal, even when they are different objects in memory.

<br>

> **Note:** By default, the equality operator (`==`) performs value equality for built-in value types and reference equality (identity) for reference types. However, user-defined value types (structs) do not automatically support the `==` operator, and specific reference types override this behavior.

<br>

You can also use the `with` expression to create a new record instance from an existing one.
```C#
var animal1 = new Animal("dog", "black");
var animal2 = animal1 with { Color = "white"};
Console.WriteLine(animal2); // Animal { Species = dog, Color = white }

public record Animal(string Species, string Color);
```

You can read more on Tuples and types here &rarr; [Microsoft's official Learn C# Guide | Tuples and Types](https://learn.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/tutorials/tuples-and-types#tuples) and a deep dive on _Records_ here &rarr; [Microsoft's official Learn C# Guide | Records](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/records)

<br>
<br>

### Arrays
Arrays are fixed length collections which serve as rigid _Lists<T>_. It's useful for precision or performance when you know the amount won't change. This may be confusing if you are coming from a language such as _JavaScript_ where arrays are flexible; in _C#_ `List<T>` are very similar to the JavaScript `Array`.

```C#
string[] bestFriends = ["Larry", "Curly", "Moe"];
```

<br>
<br>

### List\<T> (List of T)
The `List<T>` type stores sequences of elements; you specify the type of the elements between the angle brackets. Unlike the [array](#arrays) type which has a fixed length, the `List<T>` type can grow or shrink, so you can `Add()` or `Remove()` elements. It's the same thing as a JavaScript `Array` but with a different name.

<br>

**Try running the following code to see the output.**
```C#
// Initialize the alphabet to loop over
List<char> alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'];

// The sentence we will use to count letter occurrences.
string sentence = "The quick brown fox jumps over the lazy dog.";

// A dictionary to keep track of how many times each letter appears.
var alphabetCount = new Dictionary<char, int> {};

Console.WriteLine("Analyze the following sentence: " + sentence + ".");
Console.WriteLine($"That sentence has a total of {sentence.Count() - 9} letters.");
Console.WriteLine($"It includes every letter of the alphabet but has {(sentence.Count() - 9) - 26} extra letters.");
Console.WriteLine("So what are those extra letters? Well, let's count all of them");
Console.WriteLine("----------------------------");

// Count and store counts inside of our dicitonary.
foreach(char letter in alphabet)
{
    int amount = sentence.Count(l => l == letter);
    alphabetCount.Add(letter, amount);
};

// Log each letter with their rate of occurrence.
foreach (var (key, value) in alphabetCount)
{
    Console.WriteLine($"{key} => {value}");
};
```

<br>

#### Accessing index
Easily access an element in a collection via its index. Use square bracket notation to target the element, use the caret (`^`) symbol to start from the end where `[0]` means the first element in 0-indexed collections and `^1` targets the last element.

```C#
string[] bestFriends = ["Larry", "Curly", "Moe"];
Console.WriteLine(bestFriends[0]); // Larry
Console.WriteLine(bestFriends[^1]); // More
```

<br>

#### Count
Counts the amount of elements in a collection.

```C#
List<string> users = ["Jim", "Pam", "Michael", "Dwight", "Stanley"];
Console.WriteLine(users.Count); // Outputs: 5
```

<br>

#### Add
Adds an item to a collection.

```C#
List<string> users = ["Jim", "Pam", "Michael", "Dwight", "Stanley"];
users.Add("Holly");

// Outputs Jim Pam Michael Dwight Stanley Holly (on their own lines)
foreach (string u in users)
{
    Console.WriteLine(u);   
}
```

<br>

#### Remove
Removes an item from a collection.

```C#
List<string> users = ["Jim", "Pam", "Michael", "Dwight", "Stanley"];
users.Remove("Jim");

// Outputs Pam Michael Dwight Stanley (on their own lines)
foreach (string u in users)
{
    Console.WriteLine(u);   
}
```

<br>

#### Contains
Determines whether an element is in the `List<T>`.

```C#
List<string> users = ["Jim", "Pam", "Michael", "Dwight", "Stanley"];
Console.WriteLine(users.Contains("Pam")); // Outputs: true
Console.WriteLine(users.Contains("pam")); // Outputs: false
```

<br>

#### Sort
Sorts the elements or a portion of the elements in the `List<T>` on the spot. It returns `void` so you cannot _log_ it directly.

```C#
// ✅ List is sorted alphabetically by default then logged.
List<string> users = ["Jim", "Pam", "Michael", "Dwight", "Stanley"];
users.Sort();
foreach (string user in users)
{
    Console.WriteLine(user);
}

// ❌ Invalid, will not compile.
Console.WriteLine(users.Sort());

// A quick way to sort by descending is to use Sort() -> Reverse()
List<int> numbers = [2, 1, 5, 7, 10];
numbers.Sort();
numbers.Reverse();
foreach (int num in numbers)
{
    Console.WriteLine(num);
}
```

<br>

#### IndexOf
Gets the index of an element in the `List<T>`.

```C#
List<string> users = ["Jim", "Pam", "Michael", "Dwight", "Stanley"];
Console.WriteLine(users.IndexOf("Michael")); // Outputs: 2
Console.WriteLine(users.IndexOf("michael")); // ⚠️ Outputs: -1 since it does not exist.
```

> **Note:** You might not know if an item is in the list, so always check the index returned by `IndexOf()`. If it's `-1`, the item wasn't found.

<br>

#### Clear
Removes all elements from the `List<T>`.

```C#
List<string> users = ["Jim", "Pam", "Michael", "Dwight", "Stanley"];
users.Clear();
Console.WriteLine(users.Count); // Outputs: 0
```

<br>
<br>

### Dictionary<TKey,TValue>
A Dictionary is a representation of a collection of keys and values.

```C#

```

<br>
<br>

### Branches and Loops
Branches and loops are the core control flow mechanisms in C# that dictate how code executes based on conditions or repetitions. Without them, your program would simply run sequentially from top to bottom.

> In C# code indentation is for human readers. The language doesn't treat indentation or white space as significant.

<br>

#### If Statement
The `if` statement allows you to evaluate a condition as either `true` or `false` and execute code accordingly. The condition is always wrapped in parentheses `()`.

> **Note:** C# is a strongly typed language, unlike JavaScript there is no such thing as _truthy_ or _falsy_. Conditions must be explicit booleans or implicitly converted to `true` or `false`. That's also why there is no _strict_ equality operator like in JS, there isn't a need.

<br>

```C#
int gasInLitres = 10;
int distanceInKM = 100;

// ✅ Using curly braces is recommended for clarity and to avoid accidentally adding a statement that is not scoped to the condition branch.
if (gasInLitres > 25)
{
    Console.WriteLine("Time to hit the road!");
}
else
{
    Console.WriteLine("You are running low on gas, you won't make it at this rate.");
}

// ⚠️ This is functional but risks making a mistake by adding a line after that always runs.
// This syntax only allows one statement immediately following the condition/else.
int bucketCapacityInLitres = 10;
int litresOfWater = 8;

if (litresOfWater < bucketCapacityInLitres)
    Console.WriteLine("Keep filling...");
else
    Console.WriteLine("Bucket is full!");
    Console.WriteLine("I SAID STOP THE BUCKET IS FULL!!!"); // ⚠️ This will always run!
```

<br>

#### Switch Statement
A `switch` statement executes the statements in the first _switch_ section whose case pattern matches the expression. You can accomplish the same thing with an `if` statement but <mark style="background-color: #c48ac1">&nbsp;_switch_ statements are useful for testing a **single** variable against multiple values.&nbsp;</mark> `if` statements are intended for more flexible use. In **C#** all case sections must end with the `break` keyword, the compiler enforces this rule and will raise an error if it is omitted. This is to prevent _fall-through_ where the execution from one case can flow to another. The same is true for the `default` case.

> **Note:** Each `case` must be a compile-time constant, not a variable that can change at runtime. Also, you can use the `return` and `throw` statements to pass control out of a switch statement and avoid `break`. Read more here &rarr; [Microsoft's official Learn C# Guide | Selection statements](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements#the-switch-statement)

<br>

```C#
const int YearOfBirth = 1996;
int currentYear = 2026;

// ✅ Valid Switch Statement
switch (currentYear)
{
    // This will not execute
    case < YearOfBirth:
        Console.WriteLine("You aren't even born yet!");
        break;

    // This will execute
    case > YearOfBirth:
        Console.WriteLine("You were already born!");
        goto default; // This avoids the need for `break` and executs the `default:` as well!

    // Optional fallback if none of the cases match. Can be placed in any order but typically at the end.
    default:
        Console.WriteLine("I can't figure out if you were born yet or not...");
        break;
}

// ❌ This is invalid because `currentYear` is not a compile-time constant and may change.
switch (YearOfBirth)
{
    case > currentYear:
        Console.WriteLine("You aren't even born yet!");
        break;
    
    // etc...
}
```

<br>

#### While
Loops are an important concept for creating larger programs as they allow you to execute statements more than once. Paired with `if` statements, this concept is very powerful for repeating operations that rely on a condition. The `while` statement checks a condition and executes the statement following the `while`.

```C#
int bossHealth = 100;
int heroDamage = 10;

Console.WriteLine($"You encounter a boss with {bossHealth} HP, you prepare for battle.");
while (bossHealth > 0)
{
    bossHealth -= heroDamage;
    Console.Write($"You deal {heroDamage} damage. ");

    if (bossHealth == 0)
    {
        Console.WriteLine($"The boss struggles to fight back as he drops to his knees in agony. His HP has reached {bossHealth}.");
    }
    else
    {
        Console.WriteLine($"The boss continues to fight back with {bossHealth} HP.");
    }
}
Console.WriteLine($"The boss lets out a final scream as it perishes, you have vanquished the boss!");

/* OUTPUT
 * You encounter a boss with 100 HP, you prepare for battle.
 * You deal 10 damage. The boss continues to fight back with 90 HP.
 * You deal 10 damage. The boss continues to fight back with 80 HP.
...
 * You deal 10 damage. The boss continues to fight back with 10 HP.
 * You deal 10 damage. The boss struggles to fight back as he drops to his knees in agony. His HP has reached 0.
 * The boss lets out a final scream as it perishes, you have vanquished the boss!
 */
```

<br>

#### Do While
The `do{} while()` loop is nearly identical to the `while` loop except no matter what it will always execute the code within the curly braces **once** before checking to see if the condition has been satified since the code blcok comes before the `if` statement.

```C#
int bossHealth = 100;
int heroDamage = 10;

Console.WriteLine($"You encounter a boss with {bossHealth} HP, you prepare for battle.");
do
{
    bossHealth -= heroDamage;
    Console.Write($"You deal {heroDamage} damage. ");

    if (bossHealth == 0)
    {
        Console.WriteLine($"The boss struggles to fight back as he drops to his knees in agony. His HP has reached {bossHealth}.");
    }
    else
    {
        Console.WriteLine($"The boss continues to fight back with {bossHealth} HP.");
    }
}
while (bossHealth > 0);
Console.WriteLine($"The boss lets out a final scream as it perishes, you have vanquished the boss!");

/* OUTPUT
 * You encounter a boss with 100 HP, you prepare for battle.
 * You deal 10 damage. The boss continues to fight back with 90 HP.
 * You deal 10 damage. The boss continues to fight back with 80 HP.
...
 * You deal 10 damage. The boss continues to fight back with 10 HP.
 * You deal 10 damage. The boss struggles to fight back as he drops to his knees in agony. His HP has reached 0.
 * The boss lets out a final scream as it perishes, you have vanquished the boss!
 */
```
<br>

#### For Loops
A traditional `for` loop organizes everything you need to repeat a task on a single line: a **starting point** (counter), a **rule** to decide when to stop (condition), and a step to move to the next item (**iterator**).

> **Note:** The first section of a for loop must be an expression like `int i = 0` or empty `;`.

<br>

```C#
int bossHealth = 100;
int heroDamage = 10;

Console.WriteLine($"You encounter a boss with {bossHealth} HP, you prepare for battle.");
for (; bossHealth > 0; bossHealth -= heroDamage)
{
    Console.Write($"You deal {heroDamage} damage. ");

    if ((bossHealth - heroDamage) == 0)
    {
        Console.WriteLine($"The boss struggles to fight back as he drops to his knees in agony. His HP has reached {bossHealth - heroDamage}.");
    }
    else
    {
        Console.WriteLine($"The boss continues to fight back with {bossHealth - heroDamage} HP.");
    }
}
Console.WriteLine($"The boss lets out a final scream as it perishes, you have vanquished the boss!");

/* OUTPUT
 * You encounter a boss with 100 HP, you prepare for battle.
 * You deal 10 damage. The boss continues to fight back with 90 HP.
 * You deal 10 damage. The boss continues to fight back with 80 HP.
...
 * You deal 10 damage. The boss continues to fight back with 10 HP.
 * You deal 10 damage. The boss struggles to fight back as he drops to his knees in agony. His HP has reached 0.
 * The boss lets out a final scream as it perishes, you have vanquished the boss!
 */
```

<br>

#### For Each
The `for each` loop repeats its statement for every item in s sequence of items, you most often use it with _collections_.

```C#
List<string> newUsers = ["Anonymous 123", "Anonymous 274", "Anonymous 251", "Anonymous 466", "Anonymous 325", "Anonymous 472"];

foreach (string user in newUsers)
{
    if (user.Contains('5'))
        Console.WriteLine($"{user} has left the chatroom.");
    else
        Console.WriteLine($"{user} has joined the chatroom.");
}

/* Outputs
 * Anonymous 123 has joined the chatroom.
 * Anonymous 274 has joined the chatroom.
 * Anonymous 251 has left the chatroom.
 * Anonymous 466 has joined the chatroom.
 * Anonymous 325 has left the chatroom.
 * Anonymous 472 has joined the chatroom.
 */
```

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
<br>

### Methods
...

<br>
<br>

### Classes
Add notes on parent classes, referred to as abstract classes if they serve no purpose alone and serve as a parent class (can look up notes on abstract classes).
Can also add abstract methods when we want the child to define it.
Also add notes on override method in child for abstract methods in parent to avoid IDE warning.
```C#
public class Cat ()
{
    // Older Syntax
    public string Meow() {return "Meow!";}

    // Newer Concise One Line Syntax
    public string Meow() => "Meow!";
}
```.
A class defines the blueprint or template.

A member is a component within that blueprint, such as a field, property, or method.

An instance (or instantiation) of the class is a concrete object created in memory that holds specific values for those members.

```C#
// See https://aka.ms/new-console-template for more information

// First hero using var and default class properties
var hero = new SuperHero();

// Second hero using explicity type and also customizing properties
SuperHero otherHero = new SuperHero() {heroName = "Moonraker", realName = "Ms Moonerson", birthday = new DateOnly(1998, 02, 14)};

// First villain using a class constructor and defining properties during instantiation.
var evilVillain = new Villain("Slowster", "Saul Slogan", new DateOnly(1989, 12, 31));

// Logging the values in a fun way.
Console.WriteLine($"On the streets, they call me {hero.heroName}, but at home they simply refer to me as the original {hero.realName}!"
  + $" For those who are closest to me, they know I was born {hero.birthday}."
);
Console.WriteLine($"\nIn the streets, they call me {otherHero.heroName}, my friends call me {otherHero.realName}!"
  + $" My family know I was born {otherHero.birthday}."
);
Console.WriteLine($"\nBEHOLD! I am the infamous {evilVillain.villainName}, I have no friends so nobody calls me {evilVillain.realName}!"
  + $" People estimate I was born around {evilVillain.dateOfBirth}."
);

// Create a superhero class
public class SuperHero
{
    public string heroName = "Speed Runner";
    public string realName = "Mr Quick";
    public DateOnly birthday = new DateOnly(2000, 1, 1);
}

// Make villan class with old constructor syntax.
public class Villain
{
    public Villain(string vName, string name, DateOnly birthday)
    {
        villainName = vName;
        realName = name;
        dateOfBirth = birthday;
    }
    readonly public string villainName;
    readonly public string realName;
readonly public DateOnly dateOfBirth;
}

// Make villan class with new primary constructor syntax from C# 12.
public class Villain(string villainName, string realName, DateOnly dateOfBirth)
{
  // If we don't include these, the "outside" world/users won't be able to access these properties.
    public string VillainName { get; } = villainName;
    public string RealName { get; } = realName;
    public DateOnly DateOfBirth { get; } = dateOfBirth;
}

```
The last example is a clear, idiomatic, and recommended way with C# 12 primary constructors.
<br>
<br>

---
## .NET
...

<br>
<br>

---
## **Glossary**

- **Asynchronous** &rarr; Non-blocking operations, code executes concurrently.
- **Synchronous** &rarr; Code executing sequentially, blocking the flow until each task finishes.
- **Compiled Language** &rarr; Source code is compiled into an executable binary (_machine code_) or intermediate format (_bytecode_) file (_finding errors during compilation_).
- **Interpreted Language** &rarr; Code is executed line-by-line and errors are detected when the code is used, no executable file typically. Many modern interpreted languages like JavaScript compile source code into an intermediate format (_bytecode_) then the interpreter executes this bytecode line-by-line, which is why some errors (_e.g. missing bracket_) are caught **before** the code starts running.
- **Strongly Typed** &rarr; Explicit type declarations e.g. `string name = "Name"` instead of `name = "Name"`.
- **Dynamically (_loose_) Typed** &rarr; Variables aren't bound to specific data types (_string can become number_).
- **Intermediate Language (IL)** &rarr; Low level, platform-independent programming language generated by a compiler. It serves as a bridge between human redable source code and raw machine code.
- **Ahead-of-Time (AOT) compilation** &rarr; A technique that translates source code into machine code **before** the execution of a program.
- **Just-in-Time (JIT) compilation** &rarr; A technique that translates source code into machine code **during** the execution of a program, rather than **before**. It combines the flexibility of an interpreted language with the speed of a compiled language.
- **Thread** &rarr; A single sequence of instructions.
- **Single-Threading/Multi-Threaded** &rarr; Single-threading executes tasks sequentially (_one at a time_); multi-threading runs multiple tasks concurrently.
- **Blocking** &rarr; Main thread stops executing code while waiting for an operation to finish (_e.g. fetch_).
- **I/O Tasks** &rarr; Network requests such as fetching and posting.
- **Language Integrated Query (_LINQ_)** &rarr; A .NET feature that integrates data querying capabilities directly into .NET languages like **C#** allowing you to filter, sort, group and transform data from diverse data sources without needing separate query languages like SQL.
- **.NET vs ASP.NET** &rarr; **.NET** is the overarching developer platform that lincudes the runtime, languages (_like C#_), and base libraries for everything from desktop apps to games. **ASP.NET** is specifically the extension of that platform used to build web applications and APIs.
- **ASP.NET Core Web API vs ASP.NET Core MVC** &rarr; **ASP.NET Core Web API** is built to create data-only services (_like JSON or XML_) for other apps to consume, while **ASP.NET Core MVC** is designed to build full-stack web applications that serve user interfaces via HTML views.
- **Blazor** &rarr; Microsoft's frontend framework. It allows you to build interactive web UIs using C# instead of JavaScript, running directly in the browser via WebAssembly
- **NuGet** &rarr; The official package manager (_like **npm**_) for the .NET ecosystem.
- **WebAssembly (__Wasm)__** &rarr; A low-level, binary instruction format that allows devs to run code written in languages like C# directly inside web browsers at near-native execution speeds.
- **.cs** &rarr; The file extension denoting a c# file.
- **...** &rarr; ...

<br>
<br>

---
## **Resources**

<br>
<br>

#### **References**

[Microsoft's Official C# Language Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/)

[Microsoft Copilot](https://copilot.microsoft.com/)

[Complete C# Masterclass by Denis Panjuta](https://www.udemy.com/course/complete-csharp-masterclass/)

[C# Cheat Sheet by Zero to Mastery (ZTM)](https://zerotomastery.io/cheatsheets/csharp-cheat-sheet/)

[Perplexity AI](https://www.perplexity.ai/)

[Google Gemini / AI Mode](https://gemini.google.com/app)

[Chat GPT](https://chatgpt.com/)

<br>
<br>

#### **Tools**

- VS Code in Browser &rarr; [GitHub Codespace](https://github.com/codespaces)
- C# Playground &rarr; [Net Fiddle](https://dotnetfiddle.net/)

<br>
<br>

---
