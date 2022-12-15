# **SQL**

> _"SQL is one of the most tested and proven languages in use, having been used in databases for over 40 years"_
>
> -Unknown

<br>
<br>

## Overview

Databases are for storing information, but in almost all cases we need to manipulate that data. We call these **CRUD** operations. The goal is to **create**, **read**, **update** and **delete** data. This guide will serve as a reminder for common SQL queries, as well as a knowledge base for SQL fundamentals.

<br>

The material I've found is a mixture of:

-   [sqltutorial.org](https://www.sqltutorial.org/)

-   Le Wagon(Kitt) Study Docs

-   Stackoverflow

-   [W3schools](https://www.w3schools.com/sql/exercise.asp)(They have some great exercises)

-   Other various websites

---

<br>

## **Quick tips & tricks**

-   To quickly view an entire table, use the `SELECT * FROM "TABLE_NAME"`
-   ...

<br>
<br>

---

## **Querying the Database**

<br>

### **SELECT Keyword**

We use the `SELECT` and `FROM` statement when we want to read data from the database. The `FROM` specifies which table to look at and the `SELECT` determines which column(s) to select. If there are multiple columns, you separate each column name with a comma(`,`). If you want all of the columns, you put an asterix(`*`). Each command is ended by a semicolon.

```sql
-- Query 1
SELECT * FROM table_name;

-- Query 2, same as above. Keywords are case-insensitive.
select * fRoM table_name;

-- Query 3
SELECT
    column_name,
    column_name2,
    column_name3,
FROM
    table_name;
```

In the real world however, it's very rare that we want to query entire tables, usually we only want specific data.

<br>
<br>

### **Arithmetic Operations while Querying**

It's also possible to perform certain math operations when retrieving data. For instance, if you want to calculate someone's salary if they receive a 5% raise.

```sql
SELECT
    first_name,
    last_name,
    salary * 1.05 -- 5% raise
FROM
    employees;
```

Which will return a modified salary column. The title of the column will specify how the results were changed, ex: `salary * 1.05`.

<br>
<br>

### **Creating an Alias**

You can also assign a cloumn an alias using the `AS` keyword. This doesn't actually change the table in the database schema, just renames the column in the result of the query. The original data isn't affected either.

```sql
SELECT
    first_name,
    last_name,
    salary * 1.05 AS new_salary -- multiples salary and renames it to new_salary
FROM
    employees;
```

<br>
<br>

### **ORDER BY clause**

`ORDER BY` is an optional clause of the `SELECT` statement. It allows you to sort the data returned by the `SELECT` clause in ascending or descending order. It's also possible to order by date.

```sql
SELECT
	employee_id,
	first_name,
	last_name
FROM
	employees
ORDER BY
	last_name, -- First sorts by last name (A-Z)
	employee_id; -- Then sorts by employee id (if 2 employees have the same last name for instance.)
```

<br>

If you don't specify if it should sort the data in **ascending** or **descending** order, the default is `ASC`.

```sql
SELECT
	employee_id,
	first_name,
	last_name
FROM
	employees
ORDER BY
	last_name DESC; -- sorts in descending order instead (Z-A).
```

<br>
<br>

### **DISTINCT Operator**

You can use the `DISTINCT` operator with the `SELECT` clause to filter out any duplicate data. This does not affect the acctual database data. If you selet more than one column, it will use that combination of selected columns when filtering out duplicate data.

```sql
SELECT DISTINCT
    -- If multiple people have the same job and salary, only 1 will be selected.
    job_id,
    salary,
FROM
    employees;
```

<br>
<br>

---

## **Fundamentals**

SQL is a declarative language that was designed with non-technical people in mind. A declarative language syntax focuses on specifying the result of what you want as opposed to an imperative language which focuses on giving the computer an explicit sequence of commands to perform. It reads like a natural language ex: `SELECT first_name FROM employees` and always begins with a verb that describes the action, such as `UPDATE` or `DELETE`.

<br>

![Example of SQL terminology and syntax](img/sql/syntax.png)
_Image from sqltutorial.org_

<br>
<br>

### **Comments**

Comments, just like in any programming language, is code that is ignored by the computer. In SQL, you can create a comment by using 2 dashes(or hyphens) `--` which tells the database to ignore this. Comments are very useful for documentation.

```sql
-- This is a comment. This will be ignored by the database, like a ninja 🥷🏽.
```

<br>

You can also create a multi-line comment using 2 asterixs wrapped in forward slahes (`/**/`).

```sql
/*
All of this;
will be
-- ignored
*/
```

<br>
<br>

### **Commands**

We use commands to tell SQL what we want to do, at the end of each command we put a semicolon`;` to indicate the end of the command. When writing commands, it's common to add a new line (_since it won't affect the command_) after each verb for readability.

```sql
-- First command
SELECT *
FROM TABLE_NAME_HERE
WHERE first_name = 'Denzel';

-- Second command
DELETE * FROM TABLE_NAME_HERE WHERE last_name = 'Braithwaite';
```

Commands are composed of [literals](#literals), [keywords](#keywords), [identifiers](#identifiers) or [expressions](#expressions). We call all of these `tokens` and tokens can be separated by spaces, tabs or new lines.

<br>
<br>

### **Literals**

Literals (also called **constants**), are explicit values that are either string(`'wrapped in quotes'`), numeric or binary.

```sql
'John' -- string
'26' -- string
26 -- numeric
-26.9 -- numeric
x'01' -- Binary, using x'0000' notation
```

<br>
<br>

### **Keywords**

Keywords are reserved words that cannot be used as names for tables, columns, indexes or any other database object. Some common examples you'll see are the **verbs** that are at the beginning of commands, such as `SELECT`, `INSERT` and `DROP`. To make SQL commands more readable, it's common to type keywords uppercased, but this is not necessary.

<br>
<br>

### **Identifier**

Identifiers refer to specific objects in the database such as tables and columns.

```sql
SELECT first_name -- SELECT is the keyword, first_name is the identifier (column)
FROM users; -- FROM is the keyword, users is the identifier (table)
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
