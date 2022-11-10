# **PHP**

> _"Quote"_
>
> -Anonymous

<br>
<br>

## Overview

This guide is for php.

1. A _knowledge base_ of all fundamentals

2. Reference points for best tips and practices

3. etc

<br>

The material I've found is a mixture of:

-   Udemy - PHP course [Check it out](https://www.udemy.com/course/php-for-complete-beginners-includes-msql-object-oriented/)

-   MDN docs

-   Stackoverflow

-   Other various websites

---

<br>

## **Quick tips & tricks**

-   Make sure php code is between `<?php ?>` tags.
-   Semicolons(`;`) are very important in php

<br>
<br>

---

## **Fundamentals**

White space does not matter in php.

<br>

### **Starting a PHP file**

```php
<?php
echo "Hello Planet";
?>

/* These are also acceptable, but less reliable.
<? ?>
<?= ?>
<% %>
*/
```

<mark>finish this...</mark>

<br>
<br>

### **Embedding PHP in HTML**

```php
<?php

$title = "Hello World of PHP";

<h1><?php echo $title; ?></h1>

?>
```

<mark>finish this...</mark>

<br>
<br>

### **Working with Variables**

Variables are for storing data. In PHP, we declare a variable by prepending the variable name with a dollar sign, e.g. `$variableName`. The convention is to use **lowerCamelCase**, but there are many different ways to declare a variable; however, you can't start a variable name with a number and you should avoid putting dashes in the name so it doesn't get mistaken for subtraction. Variables are also case-sensitive.

```php
<?php

$string = "I am a variable"; // String
$number = 1234567890; // Number / Integer
$alsoNumber = 3.141592654; // Floating point number

?>
```

<mark>finish this...</mark>

<br>
<br>

#### **Constants**

Constants are variables who's value never changes. Constants do not begin with a `$` sign like regular variables, and it's recommended to name a constant with uppercase letters. You can create a constant using the `define()` function, which takes 2-3 arguments.

<br>

1. **identifier:** set the name of your variable.
2. **value:** set the value of your variable.
3. **case-insensitive:** Determines if the name is case-insensitive, default is **false** **\***(_Optional_)**\***.

<br>

```php
<?php

// define("BIRTH_DATE", 1996, false);
define("BIRTH_DATE", 1996);
echo BIRTH_DATE; // Outputs 1996

?>
```

<br>

As of PHP 5.6, it's now possible to use the `const` keyword to define constants, and instead of it only being able to hold **scalar** data (_booleam, integer, floar and string_), it's now possible to create a constant array.

```php
<?php

// const COUNT_DRACULA = array(1, 2, 3, 'ah', 'ah', 'ah');
const COUNT_DRACULA = [1, 2, 3, 'ah', 'aahh', 'aaahhh'];
echo COUNT_DRACULA[3]; // Outputs 'ah'

?>
```

<mark>finish this...</mark>

<br>
<br>

### **Working with Strings**

<br>

#### **Concatenation**

You can concatenate data with the **dot**`.` operator.

```php
<?php

$name = "Kaz";
$age = 26;

// Outputs Kaz is 26
echo $name . " is " . $age

?>
```

<br>
<br>

### **Working with Numbers** <mark>Finish this...</mark>

Numbers...Add notes on math, same basic arithmetic operations (+, -, \*, /)

```php
<?php

echo 56 + 45; // 101
echo "<br>"; // Line breaks, otherwise results appear on same line
echo 56 - 45; // 11
echo "<br>";
echo 56 * 45; // 2520
echo "<br>";
echo 56 / 45; 1.244444444
echo "<br>";
echo 45 + 34 * 45 /421 - 45; 3.6342042755344
echo "<br>";

$number1 = 12;
$number2 = 24;
echo $number1 * $number2;

?>
```

<br>
<br>

### **Arrays** <mark>Finish this...</mark>

Arrays are for storing different types of data in one variable. To access the data you need to use the element's array index.

```php
<?php

$olderArray = array(1, "2", "<h1>3</h1>");
$moreCommonArray = [1, "2", "<h1>3</h1>"];

echo $moreCommonArray[0];

?>
```

If you have big arrays and don't care about the order, but need to access data without remembering the element's index, you can use **associative arrays**. Then your data will have key-value pairs, where the index is replaced with a key.

```php
<?php

$array = ["nickname" => "Kaz", "age" => 26];
echo $array["nickname"];

?>
```

<br>
<br>

### **Conditionals**

Conditional statements determine what code will be run based on a condition. A common example of this is the `if` statement, whilch will only execute code if the code evaluates to `true`.

<br>

#### **If statement**

```php
<?php

if (5 > 4) {
    // This code will run since the condition is true
    echo "5 is greater than 4";
} elseif (4 < 5) {
    // This is true but ignored since a condition was already met.
    echo "4 is less than 5";
} else {
    // This will only run of no conditions are true
    echo "Numbers confuse me";
};

?>
```

<br>
<br>

### **Switch Statements**

Switch statements are similar to if statements but depending on the situation, it might make more sense to use a switch statement instead of **multiple** if statements, for readability. They're especially useful when you want to test <mark>1 statement on multiple values.</mark>

When writing a switch statement, it's important to remember to use the `break` keyword after each condition, otherwise if it matches a condition, it will execute <mark>every line of code below it, within the switch statement.</mark>

```php
<?php

$meaningOfLife = 42;

switch ($meaningOfLife) {
    case 34:
        // This will not execute because 34 != 42
        echo "The meaning of life is 34? Is that right?";
        break;
    case 42:
        // This will execute since 42 == 42
        echo "The meaning of life, the universe and everything.";
        break;
    case 69:
        // This will not execute because 69 != 42
        echo "The meaning of life is certainly not 69...";
        break;
};

?>
```

<br>
<br>

### **Comparison and Logical Operators**

Comparison and logical operators are very useful when using conditional statements.

<br>

#### **Comparison Operators**

```php
<?php
/*
== is equal to
=== is identical to
!= is not equal to
*/
?>
```

<br>
<br>

#### **Logical Operators**

```php
<?php
/*
&& and
|| or
*/
?>
```

<br>
<br>

### **Loops**

Loops allow us to repeat code until a certain condition is met.

<br>

#### **While Loop**

The while loop will continue while a certain condition is true. To avoid infinite loops, typically you'd create a **counter** variable and increment it for each loop. What's important is that your condition will eventually become false.

```php
<?php
$lemonade = 5;
while ($lemonade <= 10) {
    echo "Give me some lemonade for {$lemonade} cents please.<br>";
    // $lemonade = $lemonade + 1;
    // $lemonade += 1;
    $lemonade ++;
};

/* Outputs:
Give me some lemonade for 5 cents please.
Give me some lemonade for 6 cents please.
Give me some lemonade for 7 cents please.
Give me some lemonade for 8 cents please.
Give me some lemonade for 9 cents please.
Give me some lemonade for 10 cents please.
*/

?>
```

<br>
<br>

#### **For Loop**

`while` loops and `for` loops essentially do the same thing, but difference lies in the arguments passed. In a `while` loop you're checking for a condition, but in a for loop you must provide 3 important things.

1. A counter variable
2. A condition for that counter
3. How much to increment or decrement the counter

So `for` loops are useful when you know how many times you'd like to iterate(loop).

```php
<?php

// I counted down here as an example, but I could've incremented.
echo "Count down commencing...<br>";
for ($counter = 10; $counter >= 0; $counter--) {
    echo "{$counter}<br>";
};
echo "! This message will now self-destruct !";

/* Outputs:
Count down commencing...
10
9
8
7
6
5
4
3
2
1
0
! This message will now self-destruct !
*/

?>
```

<br>
<br>

#### **Foreach Loop**

The `foreach` loop only works with arrays. It goes through the entire array and stops without us having to specify a condition for the loop to end.

```php
<?php

$animeList = ["Death Note", "One Piece", "Naruto", "Cowboy Bebop"];

foreach ($animeList as $anime) {
    echo $anime . "<br>";
};
/* Outputs:
Death Note
One Piece
Naruto
Cowboy Bebop
*/

?>
```

<br>
<br>

### Functions

Functions are a great way to reuse parts of your code instead of having to retype it over and over again. We create a function that has one job, and then we **_call_** that function whenever we need it. Functions may have parameters and may return a value, but these aren't necessary.

```php
<?php

// Let's say it takes 4 apples to make one drink.
function appleJuicer($amount) {
    echo "Thanks for the {$amount} apples<br>";
    $glasses = $amount / 4;
    if ($glasses < 1) {
        echo "This isn't enough to make a full glass of juice...<br>";
    } else {
        echo "With this I can make " . ceil($glasses) . " glasses of juice!<br>";
    };
};

appleJuicer(1); // This isn't enough to make a full glass of juice...
appleJuicer(4); // With this I can make 1 glasses of juice!
appleJuicer(8); // With this I can make 2 glasses of juice!


// Example of a function that returns a value
function square($number) {
    return $number * $number;
}

$numberSquared = square(2);
echo $numberSquared; // Outputs 4

$numberSquared = square(4);
echo $numberSquared; // Outputs 16

?>
```

<br>
<br>

### **Scope**

The scope determines where variables can be accessed from. There's global and local scope. In PHP, something declared in the global scope, cannot be accessed within a local scope unless we use the `global` keyword. A variable inside of the local scope can only be accessed from within its scope.

```php
<?php

$secretIdentity = "Superman";

function unmask () {
    global $secretIdentity; // Allows the variable to be accessed within the local scope
    $secretIdentity = "Clark Kent";
};

echo $secretIdentity . "<br>"; // Outputs "Superman"
unmask();
echo $secretIdentity; // Outputs "Clark Kent"

?>
```

Had we not used the `global` keyword, it would've created a new local scoped variable within the function. Then it would've never updated the global variable, so it would've echoed `"Superman"` twice.

<br>
<br>

---

## **Resources**

<br>
<br>

#### **`Documentation`** <mark>finish this...</mark>

For a more complete guide with more examples, visit:

<br>

[website]()

<br>
<br>

---
