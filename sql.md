# **SQL**

> _"SQL is one of the most tested and proven languages in use, having been used in databases for over 40 years"_
>
> -Unknown

<br>
<br>

## Overview

Databases are for storing information, but in almost all cases we need to manipulate that data. We call these **CRUD** operations. The goal is to **create**, **read**, **update** and **delete** data. This guide will serve as a reminder for common SQL queries, as well as a knowledge base for SQL fundamentals. For many (_but not all_) examples in this guide, we'll use a sample database from [sqltutorial.org](https://www.sqltutorial.org/).

![sample database](img/sql/sample_db.png)

<br>

The material I've found is a mixture of:

-   [sqltutorial.org](https://www.sqltutorial.org/)

-   Le Wagon (_Kitt_) Study Docs

-   Stackoverflow

-   [W3schools](https://www.w3schools.com/sql/exercise.asp) (_They have some great exercises_)

-   [Oracle](https://www.oracle.com/ca-en/database/)

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

### **Group BY clause**

`GROUP BY` is an optional clause of the `SELECT` statement. It's usually used with [aggregate functions](#aggregate-functions) (_such as `min` and `sum`_) which is covered further below. Without an affregate function, `GROUP BY` behaves just like `DISTINCT`. The goal is to group similar data together and remove duplicate info. For instance, you have a company and you want to know the minimum salary your employees are making by department. You don't need the name of every single employee who's making that minimum salary, you just want to know what that number is.

<br>

In this example, you'd like to find the **minimum** salary per department, that's all. But if the db (_database_) table only has a `salary` column, you'll need to use the `MIN()` [aggregate function](#aggregate-functions), which finds the minimum amount in the specified column. But a `departments` table wouldn't include the salary info of every employee (_think of one-to-many relationships, every employee belongs to a dept. but a dept. has many employees_), so you'll need to join the `departments` table on the `employees` table.

<br>

_Snippet from sample db_

![tables from db sample](img/sql/small_db_sample.png)

```sql
SELECT
  d.department_name,
  MIN(salary) AS min_salary -- AS keyword optional, added for clarity
FROM
  employees e
INNER JOIN
  -- also valid: departments d ON e.department_id = d.department_id
  departments d ON d.department_id = e.department_id
GROUP BY
  department_name;
```

<br>

**Results:**

![online sql db tool with sample query](img/sql/online_sql_tool_example.png)

_This example was inspired by a **slightly** more complicated example found here on [sqltutorial.org](https://www.sqltutorial.org/sql-group-by/#:~:text=SQL%20GROUP%20BY%20with%20MIN%2C%20MAX%2C%20and%20AVG%20example) and was created using the [online sql db tool](https://www.sqltutorial.org/seeit/)_

<br>
<br>

### **LIMIT Clause**

Sometimes you only want to select a specific amount of columns, in which case you can use the `LIMIT` clause as well as the `OFFSET` clause to determine where to start counting and how many rows to show. `LIMIT` can be used alone but `OFFSET` can only be used with `LIMIT`.

```sql
SELECT
    min_salary,
    max_salary
FROM
    jobs
WHERE
    min_salary >= 5000
AND
	max_salary <= 15000
ORDER BY
	max_salary DESC
LIMIT
    5
OFFSET -- I'm not sure why OFFSET isn't being color coded here.
	3;
```

<br>

Since the offset is **3**, the query will skip the first **3** results it would've returned and instead return the next **5** (since the limit is **5**) rows. You can also use the shorthand expression `LIMIT 3, 5` to set the `OFFSET` to **3** and the `LIMIT` to **5**.

![example of sql limit and offset shorthand expression](img/sql/limit_offset_shorthand.png)
_Image taken from sqltutorial.org_

<br>

`LIMIT` is widely supported by many database systems, however, it's not in SQL standard, so it's technically not 100% supported. For an alternative and more reliable option, use `FETCH`. You can read more on fetch [here](https://www.sqltutorial.org/sql-fetch/).

<br>
<br>

### **WHERE Clause**

The `WHERE` clause let's you set a condition for the data you want returned. For instance, what if you only wanted data **where** the salary is above a certain amount, or employees **where** their last name starts with a '**B**'. You can achieve this result by using comparison operators in your query.

`*` _Note that it's impossible to test if something is `= NULL` since the expression will always return false. Instead use `IS NULL` not `= NULL`._

<br>

#### **Comparison Operators**

![Table of sql comparison operators](img/sql/comparison_operators.png)
_Image taken from sqltutorial.org_

<br>

```sql
SELECT
    employee_id,
    first_name,
    last_name,
    salary
FROM
    employees
WHERE
    salary <= 20000
AND
    -- LIKE is covered later in the guide
    last_name LIKE 'B%';
```

In the query above, we search in the **employees** table for employees who's salary is **less than or equal to** $20,000 **and** who's last name begins with the letter **B**. From those results we want to display 4 columns: **employee_id**, **first_name**, **last_name** and **salary**. It would also be possible to compare 2 columns against eachother, ex: `WHERE salary > min_salary`.

<br>
<br>

### **Logical Operators**

Logical operators allows you to test a condition and will return **true**, **false** or **unkown** like comparison operators.

![SQL logical operators](img/sql/logical_operators.png)

<br>
<br>

#### **AND**

Returns true if both expressions are true.

```sql
-- Returns all columns in the restaurants table where the price is less than 5 and the calories are under 1000.
SELECT * FROM restaurants WHERE price >= 5 AND calories <= 1000;
```

<br>
<br>

#### **OR**

Returns true if at least 1 expression is true.

```sql
-- Returns all columns in the restaurants table where the price is less than 5 or the calories are under 1000.
SELECT * FROM restaurants WHERE price >= 5 OR calories <= 1000;
```

<br>
<br>

\* _**Note:** the queries below use [subqueries](#subqueries)_ \*

#### **ALL, ANY and SOME**

-   **ALL** - Compares a value to all values in another value set. It must be preceded by a [comparison operator](#comparison-operators) and followed by a subquery.

-   **ANY** - Returns true if any one of the comparisons is true.

-   **SOME** - Returns true if some of the expressions are true.

-   **Exists** - Returns true if a subquery contains one or more rows.

<br>

_This example comes from sqltutorial.org_

```sql
SELECT
    first_name, last_name, salary
FROM
    employees
WHERE
    salary >= ALL ( -- ALL, ANY and SOME have the same syntax
        SELECT
            salary
        FROM
            employees
        WHERE
            department_id = 8
    )
ORDER BY salary DESC;

-- Usually you wouldn't type these queries on one line, for readability.
SELECT first_name FROM employees WHERE EXISTS(
    SELECT salary FROM job_salaries WHERE salary >= 10000
);
```

<br>
<br>

#### **BETWEEN**

Returns true if the searched values are within a set of values. You must also provide the minimum and maximum value to search **between**.

```sql
-- Example 1
SELECT
    employee_id, first_name, last_name
FROM
    employees
WHERE
    hire_date BETWEEN '2019/12/01' AND '2022/12/01';

-- Example 2
SELECT first_name FROM employees WHERE salary BETWEEN 1000 AND 10000;
```

<br>
<br>

#### **IN**

Returns true if the compared value matches one or more in the list.

```sql
SELECT * FROM countries WHERE country_name IN ('Canada', 'USA', 'Brazil');
```

<br>
<br>

#### **LIKE**

SQLtutorial.org describes `LIKE` as follows:

> "_The LIKE operator compares a value to similar values using a **wildcard** operator. SQL provides two wildcards used in conjunction with the `LIKE` operator._
>
> 1. The percent sign (`%`) represents zero, one, or multiple characters.
> 2. The underscore sign ( `_`) represents a single character."

```sql
-- Returns countries who START with 'CA'. Ex: Canada
SELECT * FROM countries WHERE country_name LIKE 'CA%';

-- Returns countries who END with 'CA'. Ex: America
SELECT * FROM countries WHERE country_name LIKE '%CA';

-- Returns countries who contain 'CA'. Ex: America, Zambia
SELECT * FROM countries WHERE country_name LIKE '%AM%';

-- Returns the country name if it contains AM(any single letter here)R in the name. EX: America
SELECT country_name from countries WHERE country_name LIKE '%AM_R%';
```

<br>

#### **NOT**

Reverses the result of a Boolean operator.

```sql
-- This retrieves movie titles that are NOT Titanic.
SELECT title FROM movies WHERE NOT title = 'Titanic';
```

<br>
<br>

### **Joining Tables**(_theory_)

Often, you'll need to query data from multiple tables, the only way to accomplish this is to **join those tables** together. In a relational database, we store information in tables, and when some of those tables share information, we can join them together. There's a few ways to do this, but in this section we'll assume we're performing an **`INNER JOIN`**.

<br>
<br>

Imagine you have movie rental shop (_because those existed_), and you have a database that keeps track of all of the customers and movies. In one table you can have the customer information (_customer ID number, name, address, etc_) and in the other, all the info about movies.

![sql database table](img/sql/customers_movies.png)

In this example, the customer can rent many movies and a movie can be rented by many people(_but not at the same time of course_). We call this a **many-to-many** relationship.

<br>
<br>

When we have many-to-many relationships, we usually create an additional table that has the purpose of <mark>linking those 2 tables together</mark>. For instance, this new table would be the '**rentals**' table, which keeps track of each movie id rented and the customer id that rented it. So how do we connect these tables together?

<br>

We do so with [**foreign keys**](#foreign-keys). All tables have an auto-incrementing ID column, and we can tell the database that the `customer_id` column in the customers table is the same as the `customer_id` column in the rentals table. So what's the point of this? Well many-to-many relationships can be difficult to work with, <mark>what we want is a **one-to-many** or **many-to-one** relationship.</mark>

![sql database joined tables](img/sql/joined_tables.png)

<br>
<br>

In a **one-to-many** or **many-to-one** relationship, the golden rule is it's always the <mark>**child's responsibility to carry the foreign key of the parent.**</mark> Imagine someone eating a hamburger, the hamburger can only be eaten by one person, but that person has probably eaten over 100 hamburgers in their life. It wouldn't make sense to have the **_parent_** remember all the food(**_child_**) when the food only has to remember the one person who ate it.

![database hamburger example](img/sql/hamburger.png)

But if it was a **many-to-many** relationship, both tables would have to reference each-other and keep track of every relationship. That's why it's simple to have a **one-to-many** relationship and have the child carry the parent's foreign key, then join those tables if we ever need the extra data from the child's table.

<br>
<br>

### **Joining Tables**(_practical_)

When we want to join tables together, there's a few different kinds of **joins** we can do.

<br>

-   **INNER JOIN** - combines two tables based on a **shared key**.
-   **LEFT JOIN** - returns all rows from the first table and only the rows in the second table that match(_opposite of right_).
-   **RIGHT JOIN** - returns all rows from the second table and only the rows in the first table that match(_opposite of left_).
-   **FULL OUTER JOIN** - returns all rows from both tables, as long as there is at least one match between them(_combination of left and right_).
-   etc

For more information on LEFT, RIGHT and FULL OUTER JOINs, I'd suggest you visit either [sqltutorial.org](https://www.sqltutorial.org/) or [coursera.org](https://www.coursera.org/articles/sql-join-types).

<br>
<br>

#### **INNER JOINs**

An `INNER JOIN` joins 2 or more tables together by using `foreign keys`. Consider the following **one-to-many** relationship where elves make many christmas presents but a present can only be made by one elf. In this case, the elf is the parent and the present is the child.

![elf and presents database table](img/sql/elves_presents.png)

```sql
SELECT
  elves.magical_name,
  toy_type
FROM
  presents
  INNER JOIN elves ON elves.elf_id = presents.elf_id

-- Using aliases, same query
SELECT
  e.magical_name,
  toy_type
FROM
  presents p
  INNER JOIN elves e ON e.elf_id = p.elf_id
```

<br>
<br>

### **Subqueries**

A subquery is a query nested inside another query, such as a SELECT statement. Subqueries are always written between parentheses and generally run first since that info is needed in the main sql query (_read more about [order of operations below](#order-of-operations)_).

<br>

Consider the code snippet below, both queries are the same but they're just written a bit differently (_matter of preference_) for readability.

```sql
-- Version 1
SELECT first_name, last_name
FROM employees
WHERE department_id IN (
  SELECT department_id
  FROM departments
  WHERE location_id = 1700
);

-- Version 2
SELECT
  first_name, last_name
FROM
  employees
WHERE
  department_id IN (SELECT
    department_id
  FROM
    departments
  WHERE
    location_id = 1700);
```

To read more about subqueries and get a better idea of when and how they're used, visit the subquery section of sqltutorial.org [here](https://www.sqltutorial.org/sql-subquery/).

<br>
<br>

### **Aggregate Functions**

finish me...

```sql

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

### **Aliases**

Aliases let you rename tables and columns temporarily to make your queries shorter and more understandable. If the alias contains spaces, you will need to wrap it in quotes.

<br>
<br>

#### **Assigning an alias to a column**

<br>

```sql
SELECT
-- Using the AS keyword
    department_id AS dept,
    region_id AS region
FROM
    departments;

-- Without the AS keyword
SELECT department_id dept FROM departments;

-- Without the AS keyword and with a space
SELECT department_id 'dep id' FROM departments;

-- Returns modified data and assigns the temporary column an alias.
SELECT age + 1 AS new_age FROM users;
```

<br>
<br>

Take a look at this great example of common mistakes when assigning column aliases. This is taken directly from [sqltutorial.org](https://www.sqltutorial.org/)

![common SQL alias mistake](img/sql/alias_mistake.png)

<br>
<br>

#### **Assigning an alias to a table**

<br>

Assigning an alias to a table has a similar syntax.

```sql
SELECT table_name AS alias_name ...
```

<br>

But you can also use a fully qualified name when querying a table which includes both the table and column name.

```sql
-- Syntax: SELECT table_name.column_name FROM table_name
SELECT games.title FROM games ...
```

<br>

This may seem pointless since you still have to specify the `FROM` clause with the table name, but this can be very useful when working with [joined tables](#joining-tables). It's also a good way to save keystrokes and improve readability.

<br>

_Here's an edited code snippet taken from stackexchange.com. View the [full article here](https://dba.stackexchange.com/questions/5989/is-table-aliasing-a-bad-practice)_

```sql
FROM
            billing.financial_transactions  ft_cdi   -- alias required here
INNER JOIN
            billing.cash_application_links  cal
        ON  ft_cdi.key_num = cal.applied_ft_key_num
INNER JOIN
            billing.financial_transactions  ft_pmt   -- alias required here
        ON  cal.owner_key_num = ft_pmt.key_num
LEFT OUTER JOIN
            billing.invoice_lines           invl
        ON  ft_cdi.key_num = invl.invoice_key_num
INNER JOIN
            billing.billers                 bil
        ON  ft_cdi.biller_account_key_num = bil.biller_account_key_num
INNER JOIN
            billing.formal_entities         fe
        ON  bil.frml_key_num = fe.key_num
WHERE
    ft_cdi.transaction_type <> 'Payment'   -- alias tells me this table is not for payments
AND ft_pmt.transaction_type =  'Payment';  -- alias tells me this table is for payments
```

<br>
<br>

### **Order of operations**

In any programming language, it's crucial to understand the order of operations (_which line of code will be executed first_) to avoid running into confusing errors. Take the following code snippet for example.

<br>

```sql
SELECT
  first_name,
  last_name,
  age
FROM
  students
WHERE
  age < 18
ORDER BY
  last_name, first_name;
```

In the example above, we first write `SELECT` and then later tell it `FROM` where, but the database can't select a column if it doesn't know which table it's in. So it will actually evaluate the `FROM` clause first, then when it has the table it will look at the `SELECT` to get the column. Finally it will take that column and evaluate the `WHERE` clause to filter out unwanted results. Lastly, it will order it alphabetically (`ASC` by default) by last name, and then by first name.

<br>

Here's another great example from [sqltutorial.org](https://www.sqltutorial.org/sql-alias/) in the *SQL Alias* section. It shows a common mistake when assigning a table column an alias.

![sqltutorial common column alias mistake screenshot](img/sql/sql_order_of_operations.png)

<br>
<br>

### **Data Types**

There are many data types in SQL, including `VARCHAR`, `INT` and `TEXT`. It's important to have the correct data type for your columns to insure you don't inject invalid data into your db. For a more complete list of all data types, visit this chart on [w3schools.com](https://www.w3schools.com/sql/sql_datatypes.asp).

<br>
<br>

### **Primary Keys**

All tables **should** have **only one** primary key. A primary key is a column of unique data that helps identify each row of a table, meaning it can't be a duplicate and it cant be `NULL` (_or non-existent_) either. Very commonly, tables will have an `ID` column which auto-increments making it a perfect primary key since the values are always unique.

<br>
<br>

### **Foreign Keys**

A foreign key is a reference to another table's primary key. Foreign keys are used when we want to [join tables](#joining-tablestheory) together. For instance in a one-to-many relationship, the child will carry the foreign key of the parent table. By default, an auto-incrementing column will begin at 1.

<br>

![elves and presents table](img/sql/elves_presents.png)

In the example above, each elf can make **many** presents, but a present can only be made by **one** elf, so it's the elf's (_child_) responsibility to carry the foreign key of the parent. In this case that's the `elf_id`. Notice how that's the same as the `elf_id` primary key in the elves tables.

<br>
<br>

### **Creating a Table**

The minimum requirements for creating a table is a **table name and 1 named column**. There can be no duplicate tables in the database or it will raise an error. When you create a column, you have to specify its **name** and its **type**, but you can also **optionally** specify **default values** and column [**constraints**](#constraints) (_such as a length limit_). Every table **should** absolutely have a [**`PRIMARY KEY`**](#primary-keys) and although it's **very** common that we use the `ID` column as a primary key, it's not necessary.

```sql
-- Syntax
CREATE TABLE table_name_here(
  -- If no default value for an auto-incrementing column is specified, it will start at 1.
  primary_key_column data_type_here default value column_constraints,
  column_name_here data_type_here
);

CREATE TABLE soldiers(
  soldier_id INT AUTO_INCREMENT PRIMARY KEY,
  first_name VARCHAR(25) NOT NULL,
  last_name VARCHAR(30) NOT NULL,
  age INT
);
```

<br>
<br>

### **Altering a Table**

The `ALTER TABLE` statement allows you to add new columns, modify column attributes (_such as constraints_) and remove columns. By default, if you add a column it will appear as the last column of the table. You can specify where it's inserted by using the `AFTER` clause.

```sql
ALTER TABLE soldiers
-- Then use a clause such as ADD, MODIFY or DROP.
ADD date_of_birth DATE [AFTER soldier _id];
```

<br>

Now let's change `date_of_birth` to `birth_year` and the type to `year`. Then finally, we'll drop the new column all together. Remember, when modifying columns it's entirely possible to lose data if you aren't careful. For instance, if you change a column from `INT` to `VARCHAR` **after** data is already in the table, that can cause errors during conversion.

```sql
-- Renaming column.
ALTER TABLE soldiers
RENAME COLUMN date_of_birth TO birth_year;

-- Making birth year mandatory
ALTER TABLE soldiers
MODIFY birth_year YEAR NOT NULL;

-- Deleting the column and all of its data.
ALTER TABLE soldiers
DROP COLUMN birth_year;
```

<br>
<br>

### **Dropping a Table**

The

```sql

```

<br>
<br>

### **Constraints**

Constraints are **rules** that your table or column data has to abide by to be considered valid. This avoids having bad data in a database that can't be used; for instance, imagine if someone's first and last name could be `NULL` (_non-existent_). What would be the point of retrieving their data if we don't even know who they are? There are a few constraints out there but I'll only cover `UNIQUE` and `NOT NULL` here.

<br>

#### **UNIQUE**

unique blah blah

<br>

#### **NOT NULL**

unique blah blah


<br>
<br>

**List of commonly used constraints**

![sql common contraints](img/sql/constraints.png)

_Screenshot from [mygreatlearning.com](https://www.mygreatlearning.com/blog/sql-constraints/#what)_

<br>
<br>

---

## **Resources**

<br>
<br>

### **Documentation**

-   For a more complete guide with more examples, visit [sqltutorial.org](https://www.sqltutorial.org/)

-   If you want to test certain queries or view syntax examples, check out [w3schools](https://www.w3schools.com/sql/).

-   For info on relational databases, check out [oracle](https://www.oracle.com/ca-en/database/)

-   FOr info on SQL joins, check out [coursera.org](https://www.coursera.org/articles/sql-join-types)

<br>

### **Syntax Validator**

-   Use the [EverSQL validator](https://www.eversql.com/sql-syntax-check-validator/) to check your query syntax.

<br>
<br>

---
