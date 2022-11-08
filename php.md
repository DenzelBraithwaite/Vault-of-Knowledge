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

$olderArray = array(1, '2', '<h1>3</h1>');
$moreCommonArray = [1, '2', '<h1>3</h1>'];

echo $moreCommonArray[0];

?>
```

If you have big arrays and don't care about the order, but need to access data without remembering the element's index, you can use **associative arrays**. Then your data will have key-value pairs, where the index is replaced with a key.

```php
<?php

$array = ['nickname' => 'Kaz', 'age' => 26];
echo $array['nickname'];

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

if (5 > 4){
    // This code will run since the condition is true
    echo "5 is greater than 4";
} elseif (4 < 5){
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

switch ($meaningOfLife){
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

### **While Loop**

Loops allow us to repeat code until a certain condition is met.

```php
<?php

while () {

}

?>
```

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
