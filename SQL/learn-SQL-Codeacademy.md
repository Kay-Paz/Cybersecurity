# [Learn SQL from Codeacademy](https://www.codecademy.com/learn/learn-sql)
###### *Part of SAVVY Coders' Data Analytics & Python Pre-Work*



#### SQL Cheatsheets from Codeacademy:
- [Manipulation](https://www.codecademy.com/learn/learn-sql/modules/learn-sql-manipulation/cheatsheet)
- [Queries](https://www.codecademy.com/learn/learn-sql/modules/learn-sql-queries/cheatsheet)
- [Aggregate Functions](https://www.codecademy.com/learn/learn-sql/modules/learn-sql-aggregate-functions/cheatsheet)
- [Multiple Tables](https://www.codecademy.com/learn/learn-sql/modules/learn-sql-multiple-tables/cheatsheet)


***

## Introduction to SQL

> [SQL](https://www.codecademy.com/resources/docs/sql/about-sql), ***Structured Query Language***, is a programming language designed to manage data stored in [**relational databases**](https://www.codecademy.com/resources/docs/general/relational-database?page_ref=catalog).  
> SQL operates through simple, declarative statements. This keeps data accurate and secure, and helps maintain the integrity of [databases](https://www.codecademy.com/resources/docs/general/database?page_ref=catalog), regardless of size.
>
> The SQL language is widely used today across web frameworks and database applications. Knowing SQL gives you the freedom to explore your data, and the power to make better decisions. By learning SQL, you will also learn concepts that apply to nearly every data storage system.
>
> The statements covered in this course use **SQLite Relational Database Management System [(RDBMS)](https://www.codecademy.com/articles/what-is-rdbms-sql)**. You can also access a [glossary](https://www.codecademy.com/article/sql-commands) of all the SQL commands taught in this course.

***

## Manipulation

- A **relational database** is a *database that organizes information into one or more tables*. Here, the relational database contains one table.
- A **table** is a collection of data organized into rows and columns. Tables are sometimes referred to as *relations*.
- All data stored in a relational database is of a certain [data type](https://www.codecademy.com/resources/docs/sql/data-types?page_ref=catalog). Some of the most common **data types** are:
  - `INTEGER`, a positive or negative whole number
  - `TEXT`, a text string
  - `DATE`, the date formatted as YYYY-MM-DD
  - `REAL`, a decimal value  


```SQL
SELECT * FROM celebs;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/389c2d3d-cb4f-4071-a508-b60557fae0c9)

The first row in the celebs table has:
- An `id` of `1`
- A `name` of `Justin Bieber`
- An `age` of `22`

### Statements

The code below is a SQL statement. A **statement** is text that the database recognizes as a valid command. Statements always end in a semicolon `;`.

```SQL
CREATE TABLE table_name (
   column_1 data_type, 
   column_2 data_type, 
   column_3 data_type
);
```

Components of the statement:

- `CREATE TABLE` is a **clause**.
  - Clauses perform specific tasks in SQL.
  - By convention, clauses are written in capital letters.
  - Clauses can also be referred to as *commands*.
- `table_name` refers to the name of the table that the command is applied to.
- `(column_1 data_type, column_2 data_type, column_3 data_type)` is a **parameter**.
  - A parameter is a list of columns, data types, or values that are passed to a clause as an argument.
    - Here, the parameter is a list of column names and the associated data type.

The structure of SQL statements vary. The number of lines used does not matter. A statement can be written all on one line, or split up across multiple lines if it makes it easier to read.

Let's break down the statement we previously wrote:
```SQL
SELECT * FROM celebs;
```
- Which parts of the statement are the clauses?
  - `SELECT`
  - `FROM`
- What table are we applying the command to?
  - `celebs`

> I believe the asterisk * would be considered a parameter as it's being used as a wildcard to mean "all".*

### CREATE

```SQL
CREATE TABLE celebs (
   id INTEGER, 
   name TEXT, 
   age INTEGER
);
```

1. `CREATE TABLE` is a **clause** that tells SQL you want to *create a new table*.
2. `celebs` is the name of the table.
3. `(id INTEGER, name TEXT, age INTEGER)` is a **list of parameters** defining *each column, or attribute in the table and its data type*:
    - `id` is the first column in the table. It stores values of data type `INTEGER`
    - `name` is the second column in the table. It stores values of data type `TEXT`
    - `age` is the third column in the table. It stores values of data type `INTEGER`

### INSERT

The `INSERT` statement **inserts a new row into a table.** We can use the `INSERT` statement when we want to *add new records*.  

The statement below enters a record for `Justin Bieber` into the `celebs` table:

```SQL
INSERT INTO celebs (id, name, age) 
VALUES (1, 'Justin Bieber', 22);
```

1. `INSERT INTO` is a **clause** that *adds the specified row or rows*.
2. `celebs` is the table the row is added to.
3. `(id, name, age)` is a **parameter** identifying the *columns that data will be inserted into*.
4. `VALUES` is a **clause** that *indicates the data* being inserted.
5. `(1, 'Justin Bieber', 22)` is a **parameter** *identifying the values* being inserted
    - `1:` an integer that will be added to `id` column
    - `'Justin Bieber':` text that will be added to `name` column
    - `22:` an integer that will be added to `age` column

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/959d38e3-f191-4716-89cf-dd86e89d3f69)

#### Inserting Multiple Rows:

```SQL
INSERT INTO celebs (id, name, age) 
VALUES (1, 'Justin Bieber', 22);

INSERT INTO celebs (id, name, age) 
VALUES (2, 'Beyonce Knowles', 33); 

INSERT INTO celebs (id, name, age) 
VALUES (3, 'Jeremy Lin', 26); 

INSERT INTO celebs (id, name, age) 
VALUES (4, 'Taylor Swift', 26);
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/7d66c13f-76e6-414c-8546-ad3f8d31c67d)


***[Is there a shorter way to insert multiple rows in a table?](https://discuss.codecademy.com/t/is-there-a-shorter-way-to-insert-multiple-rows-in-a-table/376659?_gl=1*6qcfa6*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjU5OTcxMS44LjEuMTY5NjYwMDU4Ny41OC4wLjA.)***
> **Yes**, instead of inserting each row in a separate `INSERT` statement, you can actually *insert multiple rows in a single statement*.
>
> To do this, you can list the values for each row separated by commas, following the `VALUES` clause of the statement.
>
> Here's how it would look:

```SQL
INSERT INTO table (col1, col2, col3)
VALUES
(row1_val1, row1_val2, row1_val3),
(row2_val1, row2_val2, row2_val3),
(row3_val1, row3_val2, row3_val3);
```

### SELECT

`SELECT` statements are used to **fetch data from a database**.  

In the statement below, `SELECT` returns all data in the `name` column of the `celebs` table:

```SQL
SELECT name FROM celebs;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/cdfca520-cbb4-4644-abce-fbb568b398df)


1. `SELECT` is a **clause** that *indicates that the statement is a query*. You will use `SELECT` *every time you query data from a database*.
2. `name` specifies the *column to query data from*.
3. `FROM celebs` specifies the *name of the table to query data from*. In this statement, data is queried from the `celebs` table.

You can also query data from ***all*** columns in a table with `SELECT`:

```SQL
SELECT * FROM celebs;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/775706ee-ac50-413a-b47b-9cba50aabc89)


`*` is a special wildcard character that we have been using. It allows you to *select every column in a table without having to name each one individually*.  

Here, the **result set** contains *every column* in the `celebs` table.

`SELECT` statements *always return a new table* called the **result set**.

### ALTER

The `ALTER TABLE` statement *adds a new column to a table*. You can use this command when you want to add columns to a table.  

The statement below adds a new column `twitter_handle` to the `celebs` table:

```SQL
ALTER TABLE celebs 
ADD COLUMN twitter_handle TEXT;
```

1. `ALTER TABLE` is a **clause** that lets you make the *specified changes*.
2. `celebs` is the name of the table that is being changed.
3. `ADD COLUMN` is a **clause** that lets you *add a new column to a table*:
    - `twitter_handle` is the name of the new column being added
    - `TEXT` is the data type for the new column
4. `NULL` is a special value in SQL that *represents missing or unknown data*.
    - Here, the rows that existed before the column was added have `NULL` (∅) values for `twitter_handle`

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/e204df64-8de1-4c61-86c8-a30830498450)

```SQL
ALTER TABLE celebs 
ADD COLUMN twitter_handle TEXT;

SELECT * FROM celebs;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/988f6c9e-50b5-42c4-8bc2-bae74617124f)

### UPDATE

The `UPDATE` statement *edits a row in a table*. You can use the `UPDATE` statement when you want to *change existing records*.  

The statement below updates the record with an `id` value of `4` to have the `twitter_handle` `@taylorswift13`:  

```SQL
UPDATE celebs 
SET twitter_handle = '@taylorswift13' 
WHERE id = 4;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/3c8de7b5-5a3f-4548-8f8c-3883a291b3c8)

***[How is `ALTER` different from `UPDATE`?](https://discuss.codecademy.com/t/how-is-alter-different-from-update/376655?_gl=1*oys2dl*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjU5OTcxMS44LjEuMTY5NjYwMjIyNC42MC4wLjA.)***
> Although similar in the sense that both statements will modify a table, these statements are quite different.
>
> The `ALTER` statement is used to **modify columns**. With `ALTER`, you can *add columns, remove them, or even modify them*.
>
> The `UPDATE` statement is used to **modify rows**. However, `UPDATE` *can ONLY update A row, and CANNOT REMOVE OR ADD rows*.

### DELETE

The `DELETE FROM` statement *deletes one or more rows from a table*. You can use the statement when you want to *delete existing records*.  

The statement below deletes all records in the `celebs` table with no `twitter_handle`:  

```SQL
DELETE FROM celebs 
WHERE twitter_handle IS NULL;
```

1. `DELETE FROM` is a **clause** that lets you *delete rows from a table*.
2. `celebs` is the name of the table we want to delete rows from.
3. `WHERE` is a **clause** that lets you *select which rows* you want to delete.
    - Here we want to delete all of the rows where the `twitter_handle` column `IS NULL`.
4. `IS NULL` is a **condition** in SQL that *returns true when the value is* `NULL` *and false otherwise*.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/f23c2ad0-9674-4270-b6cc-b939d03ee8cb)

***[What if we only want to delete a specific number of rows?](https://discuss.codecademy.com/t/what-if-we-only-want-to-delete-a-specific-number-of-rows/376657?_gl=1*19ocpio*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjU5OTcxMS44LjEuMTY5NjYwMjc2NS42MC4wLjA.)***
> To delete only a specific number of rows, you can utilize the `LIMIT` statement. The **value** provided for `LIMIT` will be *how many rows to affect*.
>
> For example, this statement will only delete the first 5 rows that match the condition:

```SQL
DELETE FROM table
WHERE condition
LIMIT 5;
```

### Constraints

[Constraints](https://www.codecademy.com/resources/docs/sql/constraints?page_ref=catalog) that add information about how a column can be used are invoked after specifying the data type for a column. They can be used to tell the database to reject inserted data that
does not adhere to a certain restriction.  

The statement below sets *constraints* on the `celebs` table:  

```SQL
CREATE TABLE celebs (
   id INTEGER PRIMARY KEY, 
   name TEXT UNIQUE,
   date_of_birth TEXT NOT NULL,
   date_of_death TEXT DEFAULT 'Not Applicable'
);
```

1. `PRIMARY KEY` columns can be used to **uniquely identify the row**
    - Attempts to insert a row with an identical value to a row already in the table will result in a constraint violation which will not allow you to insert the new row
2. `UNIQUE` columns have a **different value for every row**
    - This is similar to `PRIMARY KEY` except a table can have many different `UNIQUE` columns
4. `NOT NULL` columns **must have a value**.
    - Attempts to insert a row without a value for a NOT NULL column will result in a constraint violation and the new row will not be inserted
5. `DEFAULT` columns take an additional argument that will be the assumed value for an inserted row if the new row does not specify a value for that column

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/90a9d93e-e254-4c1e-904a-fdef701f3aea)

***[What are some reasons to apply constraints to a table?](https://discuss.codecademy.com/t/what-are-some-reasons-to-apply-constraints-to-a-table/376674?_gl=1*vzznsl*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjU5OTcxMS44LjEuMTY5NjYwMzcyMy42MC4wLjA.)***
> Applying constraints to a table can be useful, and provide some important benefits such as reliability and consistency of your data.
>
> The following are a few reasons you might consider for applying constraints to a table:
>
> - **Prevent invalid data in the table**
>   - This is very important, because invalid data can cause issues and unexpected results from calculations
>     - We do not have to worry about new data being added that might otherwise violate our constraints and cause bigger issues
>
> - **Constraints can let us prevent missing data**
>   - which is usually filled as `NULL` within the table
>   - Instead of having missing values set to `NULL`, we can set constraints so that the missing values are given some default value instead, like `0`
>     - This can make some calculations easier to do
>
> - **Uniqueness**
>   - usually in the form of values like the `id`, or identifier column
>   - By using a constraint like the `PRIMARY KEY`, we can ensure that every row has their own unique `id` value

### Manipulation Review

- SQL is a programming language designed to manipulate and manage data stored in relational databases  
  - A relational database is a database that organizes information into one or more tables  
  - A table is a collection of data organized into rows and columns
- A statement is a string of characters that the database recognizes as a valid command
  - `CREATE TABLE` creates a new table
  - `INSERT INTO` adds a new row to a table
  - `SELECT` queries data from a table
  - `ALTER TABLE` changes an existing table
  - `UPDATE` edits a row in a table
  - `DELETE` FROM deletes rows from a table
- Constraints add information about how a column can be used

***

## Queries

### AS

`AS` is a keyword in SQL that allows you to **rename a column or table using an** ***alias***.

The new name can be anything you want as long as you put it inside of single quotes. Here we renamed the name column as `Titles`:

```SQL
SELECT name AS 'Titles'
FROM movies;
```

Some important things to note:

Although it’s not always necessary, it is considered best practice to surround your aliases with single quotes.
Note that this practice is *specific to SQLite*, the RDBMS used in this exercise. 

When you work with *other RDBMSs, notably PostgreSQL, no quotes or double quotes may be required* in place of single quotes.

When using `AS`, the columns are **not being renamed in the table**. **The aliases only appear in the result.**

***[Can we alias multiple columns in a single query?](https://discuss.codecademy.com/t/can-we-alias-multiple-columns-in-a-single-query/349721?_gl=1*1cc7trb*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjYwNTI5My45LjEuMTY5NjYwNjA2OC42MC4wLjA.)***
> **Yes, you can alias multiple columns at a time in the same query.**
>
> It is advisable to always include quotes around the new alias.
> Quotes are required when the alias contains spaces, punctuation marks, special characters or reserved keywords.
>
> It is simply more convenient to always include quotes around the new alias.
>
> Example:

```SQL
SELECT course_id AS "Course ID", exercise_id AS "Exercise ID"
FROM bugs;
```

### DISTINCT

`DISTINCT` is used to **return unique values in the output**. **It filters out all duplicate values in the specified column(s).**

For instance:

```SQL
SELECT tools 
FROM inventory;
```

might produce:

| tools  |
|--------|
| Hammer |
| Nails  |
| Nails  |
| Nails  |

By adding `DISTINCT` before the column name:

```SQL
SELECT DISTINCT tools 
FROM inventory;
```

the result would now be:

| tools  |
|--------|
| Hammer |
| Nails  |


**[Can we apply `DISTINCT` to a `SELECT` query with multiple columns?](https://discuss.codecademy.com/t/can-we-apply-distinct-to-a-select-query-with-multiple-columns/349723?_gl=1*o3rmh2*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjYwNTI5My45LjEuMTY5NjYwNjM1MC42MC4wLjA.)**
> **Yes, the `DISTINCT` clause can be applied to any valid `SELECT` query.**
>
> It is important to note that **`DISTINCT` will filter out all rows that are not unique in terms of all selected columns**.
>

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/84c9fc67-c0ef-4f78-8cab-cb8a71ee3b48)

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/d6a1cd70-b908-4693-a211-591944ac96ba)


### WHERE

We can restrict our query results using the `WHERE` clause in order to **obtain only the information we want**.

Following this format, the statement below filters the result set to only include top rated movies (IMDb ratings greater than 8):

```SQL
SELECT *
FROM movies
WHERE imdb_rating > 8;
```

##### How does it work?

- The `WHERE` clause filters the result set to only include rows where the following condition is true
  - `imdb_rating > 8` is the condition
    - Here, only rows with a value greater than `8` in the `imdb_rating` column will be returned
- The `>` is an operator
  - Operators create a condition that can be evaluated as either *true* or *false*

Comparison operators used with the `WHERE` clause are:
- `=` equal to
- `!=` not equal to
- `>` greater than
- `<` less than
- `>=` greater than or equal to
- `<=` less than or equal to

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/25253316-e613-4caa-9e3f-9afa69e10012)  


***[Can we compare values of two columns in a `WHERE` clause?](https://discuss.codecademy.com/t/can-we-compare-values-of-two-columns-in-a-where-clause/349724?_gl=1*157c22p*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjYwNTI5My45LjEuMTY5NjYwNjgxOS42MC4wLjA.)***
> **Yes, within a WHERE clause you can compare the values of two columns.**
>
> When comparing two columns in a `WHERE` clause, for each row in the database, it will check the value of each column and compare them.
>
> Example:

```SQL
/* 
This will return all rows where the value in the 
x column is greater than the y column value. 
*/

SELECT x, y
FROM coordinates
WHERE x > y;
```

### LIKE pt 1

`LIKE` can be a useful operator when you want to compare similar values.

The movies table contains two films with similar titles, ‘Se7en’ and ‘Seven’.

How could we select all movies that start with ‘Se’ and end with ‘en’ and have exactly one character in the middle?

```SQL
SELECT * 
FROM movies
WHERE name LIKE 'Se_en';
```

- `LIKE` is a special operator used with the `WHERE` clause to search for a specific pattern in a column
- `name LIKE` 'Se_en' is a condition evaluating the `name` column for a specific pattern
- `Se_en` represents a pattern with a wildcard character

The `_` means you can substitute any individual character here without breaking the pattern. The names `Seven` and `Se7en` both match this pattern.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/98d36e69-5cc5-4001-b959-0321beaabe56)


***[Can we apply the `LIKE` operator to values other than `TEXT`?](https://discuss.codecademy.com/t/can-we-apply-the-like-operator-to-values-other-than-text/349726?_gl=1*1mh95jp*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjYwNTI5My45LjEuMTY5NjYwNzI2OC42MC4wLjA.)***
> **Yes, you can apply the LIKE operator to numerical values as well.**
>
> Whenever you use `LIKE` however, you must always wrap the pattern within a pair of quotations, whether for matching a number or a string.
>
> Example:

```SQL
/* 
This will select movies where the id number
starts with 2 and is followed by any two numbers.
*/
SELECT * 
FROM movies
WHERE id LIKE '2__';
```

### LIKE pt 2

The percentage sign `%` is another wildcard character that can be used with `LIKE`.

This statement below filters the result set to only include movies with names that begin with the letter ‘A’:

```SQL
SELECT * 
FROM movies
WHERE name LIKE 'A%';
```

`%` is a wildcard character that matches zero or more missing letters in the pattern. 

For example:

- `A%` matches all movies with names that begin with letter ‘A’
- `%a` matches all movies that end with ‘a’

We can also use `%` both before and after a pattern:

```SQL
SELECT * 
FROM movies 
WHERE name LIKE '%man%';
```

Here, any movie that contains the word ‘man’ in its name will be returned in the result.

`LIKE` is **not case sensitive**. ‘Batman’ and ‘Man of Steel’ will both appear in the result of the query above.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/64829b42-3dae-4e0f-a57f-928020ded25b)

***[How do we search for patterns containing the actual characters "%" or "_"?](https://discuss.codecademy.com/t/how-do-we-search-for-patterns-containing-the-actual-characters-or/349727?_gl=1*l8snrl*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjYwNTI5My45LjEuMTY5NjYwNzU1Mi42MC4wLjA.)***
> When searching for a pattern containing the specific characters % or _, we can utilize the escape character `\`, similarly to its use in Python.
>
> If we want to search for these specific characters, we can simply add the escape character immediately before them.
>
> Example:

```SQL
/* 
In this pattern, we use an escape character before '%'.
This will only match "%" and not be used like the
wildcard character.

This query will match any titles that end with
' 100%'.
*/

SELECT *
FROM books
WHERE title LIKE '% 100\%';
```

### IS NULL

Unknown values are indicated by `NULL`.

It is not possible to test for `NULL` values with comparison operators, such as `=` and `!=`.

Instead, we will have to use these operators:
- `IS NULL`
- `IS NOT NULL`

To filter for all movies with an IMDb rating:

```SQL
SELECT name
FROM movies 
WHERE imdb_rating IS NOT NULL;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/5ce16281-bf77-4bb3-9113-66b459cabe25)

### BETWEEN

The `BETWEEN` operator is used in a `WHERE` clause to filter the result set within a certain range. It accepts two values that are either numbers, text or dates.

For example, this statement filters the result set to only include movies with `year`s from 1990 up to, and including 1999.

```SQL
SELECT *
FROM movies
WHERE year BETWEEN 1990 AND 1999;
```

When the values are text, `BETWEEN` filters the result set for within the alphabetical range.

In this statement, `BETWEEN` filters the result set to only include movies with `name`s that begin with the letter ‘A’ up to, but not including ones that begin with ‘J’.

```SQL
SELECT *
FROM movies
WHERE name BETWEEN 'A' AND 'J';
```

However, if a movie has a name of simply ‘J’, it would actually match. This is because `BETWEEN` goes up to the second value — up to ‘J’. So the movie named ‘J’ would be included in the result set but not ‘Jaws’.

### AND

Sometimes we want to combine multiple conditions in a `WHERE` clause to make the result set more specific and useful.

One way of doing this is to use the `AND` operator. Here, we use the `AND` operator to only return 90’s romance movies.

```SQL
SELECT * 
FROM movies
WHERE year BETWEEN 1990 AND 1999
   AND genre = 'romance';
```

- `year BETWEEN 1990 AND 1999` is the 1st condition
- `genre = 'romance'` is the 2nd condition
- `AND` combines the two conditions.

With `AND`, **both conditions must be true for the row to be included in the result**.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/0a9dad0e-93cb-46dd-87b6-9c642fa57c33)

### OR

Similar to `AND`, the `OR` operator can also be used to combine multiple conditions in `WHERE`, but there is a fundamental difference:

- `AND` operator displays a row if **all** the conditions are true
- `OR` operator displays a row if **any** condition is true

Suppose we want to check out a new movie or something action-packed:

```SQL
SELECT *
FROM movies
WHERE year > 2014
   OR genre = 'action';
```

- `year > 2014` is the 1st condition
- `genre = 'action'` is the 2nd condition
- `OR` combines the two conditions

*With `OR`, if any of the conditions are true, then the row is added to the result.*

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/45562dcb-8f2b-4064-9405-b6d68d592ba5)

### ORDER BY

It is often useful to list the data in our result set in a particular order.

We can sort the results using `ORDER BY`, either alphabetically or numerically. Sorting the results often makes the data more useful and easier to analyze.

For example, if we want to sort everything by the movie’s title from A through Z:

```SQL
SELECT *
FROM movies
ORDER BY name;
```

- `ORDER BY` is a clause that indicates you want to sort the result set by a particular column
- `name` is the specified column

Sometimes we want to sort things in a decreasing order. For example, if we want to select all of the well-received movies, sorted from highest to lowest by their year:

```SQL
SELECT *
FROM movies
WHERE imdb_rating > 8
ORDER BY year DESC;
```

- `DESC` is a keyword used in `ORDER BY` to sort the results in descending order (high to low or Z-A)
- `ASC` is a keyword used in `ORDER BY` to sort the results in ascending order (low to high or A-Z)

The column that we `ORDER BY` doesn’t even have to be one of the columns that we’re displaying.

*Note: `ORDER BY` always goes after `WHERE` (if `WHERE` is present).*

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/c930f51b-156a-4cac-a95f-2acb0e0c86d0)

### LIMIT

We’ve been working with a fairly small table (fewer than 250 rows), but most SQL tables contain hundreds of thousands of records. 
In those situations, it becomes important to cap the number of rows in the result.

For instance, imagine that we just want to see a few examples of records.

```SQL
SELECT *
FROM movies
LIMIT 10;
```

`LIMIT` is a clause that lets you specify the maximum number of rows the result set will have. This saves space on our screen and makes our queries run faster.

Here, we specify that the result set can’t have more than 10 rows.

`LIMIT` always goes at the very end of the query. Also, it is not supported in all SQL databases.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/f7324107-3015-4693-a222-448422349dbf)

### CASE

A `CASE` statement allows us to create different outputs (usually in the `SELECT` statement). It is SQL’s way of handling if-then logic.

Suppose we want to condense the ratings in `movies` to three levels:

- *If the rating is above 8, then it is Fantastic*
- *If the rating is above 6, then it is Poorly Received*
- *Else, Avoid at All Costs*

```SQL
SELECT name,
 CASE
  WHEN imdb_rating > 8 THEN 'Fantastic'
  WHEN imdb_rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END
FROM movies;
```

- Each `WHEN` tests a condition and the following `THEN` gives us the string if the condition is true
- The `ELSE` gives us the string if all the above conditions are false
- The `CASE` statement must end with `END`

In the result, you have to scroll right because the column name is very long. To shorten it, we can rename the column to ‘Review’ using `AS`:

```SQL
SELECT name,
 CASE
  WHEN imdb_rating > 8 THEN 'Fantastic'
  WHEN imdb_rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END AS 'Review'
FROM movies;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/8aa50b29-01f6-488a-8e1b-1d8e8349a2d6)

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/193c652f-5041-41c7-badb-0b24edad624d)

### Queries REVIEW

We just learned how to query data from a database using SQL. We also learned how to filter queries to make the information more specific and useful.

Let’s summarize:

- `SELECT` is the clause we use every time we want to query information from a database
- `AS` renames a column or table
- `DISTINCT` return unique values
- `WHERE` is a popular command that lets you filter the results of the query based on conditions that you specify
- `LIKE` and `BETWEEN` are special operators
- `AND` and `OR` combines multiple conditions
- `ORDER BY` sorts the result
- `LIMIT` specifies the maximum number of rows that the query will return
- `CASE` creates different outputs

***

## Aggregate Functions

### Introduction

SQL Queries don’t just access raw data, they can also perform calculations on the raw data to answer specific data questions.

Calculations performed on multiple rows of a table are called **aggregates**.

In this lesson, we have given you a table named `fake_apps` which is made up of fake mobile applications data.

Here is a quick preview of some important aggregates that we will cover in the next five exercises:

- `COUNT():` count the number of rows
- `SUM():` the sum of the values in a column
- `MAX()/MIN():` the largest/smallest value
- `AVG():` the average of the values in a column
- `ROUND():` round the values in the column

### COUNT

The fastest way to calculate how many rows are in a table is to use the `COUNT()` function.

`COUNT()` is a function that takes the name of a column as an argument and counts the number of non-empty values in that column.

```SQL
SELECT COUNT(*)
FROM table_name;
```

Here, we want to count every row, so we pass `*` as an argument inside the parenthesis.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/20b51472-38f9-42ad-836f-901f21aabe5f)

### SUM

SQL makes it easy to add all values in a particular column using `SUM()`.

`SUM()` is a function that takes the name of a column as an argument and returns the sum of all the values in that column.

What is the total number of downloads for all of the apps combined?

```SQL
SELECT SUM(downloads)
FROM fake_apps;
```

This adds all values in the `downloads` column.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/baf3a05b-d8e2-4c4a-b199-0326a084bf21)

### MAX / MIN

The `MAX()` and `MIN()` functions return the highest and lowest values in a column, respectively.

How many downloads does the most popular app have?

```SQL
SELECT MAX(downloads)
FROM fake_apps;
```

The most popular app has 31,090 downloads!

`MAX()` takes the name of a column as an argument and returns the largest value in that column. Here, we returned the largest value in the `downloads` column.

`MIN()` works the same way but it does the exact opposite; it returns the smallest value.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/56a8d1c3-9899-45b1-817b-fefd8fef19e9)

### AVERAGE

SQL uses the `AVG()` function to quickly calculate the average value of a particular column.

The statement below returns the average number of downloads for an app in our database:

```SQL
SELECT AVG(downloads)
FROM fake_apps;
```

The `AVG()` function works by taking a column name as an argument and returns the average value for that column.

### ROUND

By default, SQL tries to be as precise as possible without rounding. We can make the result table easier to read using the `ROUND()` function.

`ROUND()` function takes two arguments inside the parenthesis:

- a column name
- an integer

It rounds the values in the column to the number of decimal places specified by the integer.

```SQL
SELECT ROUND(price, 0)
FROM fake_apps;
```

Here, we pass the column `price` and integer `0` as arguments. SQL rounds the values in the column to 0 decimal places in the output.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/0b3adcee-74ae-43dd-8df7-8b1b183152e1)

### GROUP BY pt 1

Oftentimes, we will want to calculate an aggregate for data with certain characteristics.

For instance, we might want to know the mean IMDb ratings for all movies each year. We could calculate each number by a series of queries with different `WHERE` statements, like so:

```SQL
SELECT AVG(imdb_rating)
FROM movies
WHERE year = 1999;

SELECT AVG(imdb_rating)
FROM movies
WHERE year = 2000;

SELECT AVG(imdb_rating)
FROM movies
WHERE year = 2001;
```

and so on.

Luckily, there’s a better way!

We can use `GROUP BY` to do this in a single step:

```SQL
SELECT year,
   AVG(imdb_rating)
FROM movies
GROUP BY year
ORDER BY year;
```

`GROUP BY` is a clause in SQL that is used with **[aggregate functions](https://www.codecademy.com/resources/docs/sql/aggregate-functions)**. It is used in collaboration with the `SELECT` statement to arrange identical
data into groups.

The `GROUP BY` statement comes after any `WHERE` statements, but before `ORDER BY` or `LIMIT`.

#### Exercises

1. Here, our aggregate function is `COUNT()` and we arranged price into groups:

```SQL
SELECT price, COUNT(*) 
FROM fake_apps
GROUP BY price;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/8c3424fb-0f0a-45b0-abec-ebea3d90a276)

2. In the previous query, add a `WHERE` clause to count the total number of apps that have been downloaded more than 20,000 times, at each price.

```SQL
SELECT price, COUNT(*)
FROM fake_apps
WHERE downloads > 20000
GROUP BY price;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/e8b1c9fc-75f6-4d74-9778-73913cfb5bb1)

3. Write a new query that calculates the total number of downloads for each category.

Select `category` and `SUM(downloads)`.

```SQL
SELECT category, SUM(downloads)
FROM fake_apps
GROUP BY category;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/4eb41ed2-f671-4079-835f-7df4f19f2f61)

### GROUP BY pt 2

Sometimes, we want to `GROUP BY` a calculation done on a column.

For instance, we might want to know how many movies have IMDb ratings that round to 1, 2, 3, 4, 5. We could do this using the following syntax:

```SQL
SELECT ROUND(imdb_rating),
   COUNT(name)
FROM movies
GROUP BY ROUND(imdb_rating)
ORDER BY ROUND(imdb_rating);
```

However, this query may be time-consuming to write and more prone to error.

SQL lets us use column reference(s) in our `GROUP BY` that will make our lives easier.

- `1` is the first column selected
- `2` is the second column selected
- `3` is the third column selected
  
and so on.

The following query is equivalent to the one above:

```SQL
SELECT ROUND(imdb_rating),
   COUNT(name)
FROM movies
GROUP BY 1
ORDER BY 1;
```

Here, the `1` refers to the first column in our `SELECT` statement, `ROUND(imdb_rating)`.

### HAVING

In addition to being able to group data using `GROUP BY`, SQL also allows you to filter which groups to include and which to exclude.

For instance, imagine that we want to see how many movies of different genres were produced each year, but we only care about years and genres with at least 10 movies.

We can’t use `WHERE` here because we don’t want to filter the rows; we want to filter groups.

This is where `HAVING` comes in.

`HAVING` is very similar to `WHERE`. In fact, all types of `WHERE` clauses you learned about thus far can be used with `HAVING`.

We can use the following for the problem:

```SQL
SELECT year,
   genre,
   COUNT(name)
FROM movies
GROUP BY 1, 2
HAVING COUNT(name) > 10;
```

- When we want to limit the results of a query based on values of the individual rows, use `WHERE`
- When we want to limit the results of a query based on an aggregate property, use `HAVING`

`HAVING` statement always comes after `GROUP BY`, but before `ORDER BY` and `LIMIT`.

Suppose we have the query below:

```SQL
SELECT price, 
   ROUND(AVG(downloads)),
   COUNT(*)
FROM fake_apps
GROUP BY price;
```

It returns the average downloads (rounded) and the number of apps – at each price point.

However, certain price points don’t have very many apps, so their average downloads are less meaningful.

Add a `HAVING` clause to restrict the query to price points that have more than 10 apps.

```SQL
SELECT price, 
   ROUND(AVG(downloads)),
   COUNT(*)
FROM fake_apps
GROUP BY price
HAVING COUNT(*) > 10;
```

The total number of apps at each price point would be given by `COUNT(*)`.

`COUNT(*) > 10` is the condition.

Because the condition has an aggregate function in it, we have to use `HAVING` instead of `WHERE`.

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/0949817b-bc0a-4dec-bc5d-cae5579b9360)

### Aggregate Functions Review

You just learned how to use aggregate functions to perform calculations on your data. What can we generalize so far?

- `COUNT():` count the number of rows
- `SUM():` the sum of the values in a column
- `MAX()`/`MIN():` the largest/smallest value
- `AVG():` the average of the values in a column
- `ROUND():` round the values in the column

*Aggregate functions* combine multiple rows together to form a single value of more meaningful information.

- `GROUP BY` is a clause used with aggregate functions to combine data from one or more columns
- `HAVING` limit the results of a query based on an aggregate property

***

## Multiple Tables

### Introduction

In order to efficiently store data, we often spread related information across multiple tables.

For instance, imagine that we’re running a magazine company where users can have different types of subscriptions to different products. Different subscriptions might have many different properties. Each customer would also have lots of associated information.

We could have one table with all of the following information:

- `order_id`
- `customer_id`
- `customer_name`
- `customer_address`
- `subscription_id`
- `subscription_description`
- `subscription_monthly_price`
- `subscription_length`
- `purchase_date`

However, a lot of this information would be repeated. If the same customer has multiple subscriptions, that customer’s name and address will be reported multiple times. If the same subscription type is ordered by
multiple customers, then the subscription price and subscription description will be repeated. This will make our table big and unmanageable.

So instead, we can split our data into three tables:

1. `orders` would contain just the information necessary to describe what was ordered:
    - `order_id, customer_id, subscription_id, purchase_date`
2. `subscriptions` would contain the information to describe each type of subscription:
    - `subscription_id, description, price_per_month, subscription_length`
3. `customers` would contain the information for each customer:
    - `customer_id, customer_name, address`

In this lesson, we’ll learn the SQL commands that will help us work with data that is stored in multiple tables.

```SQL
SELECT *
FROM orders
LIMIT 5;

SELECT *
FROM subscriptions
LIMIT 5;

SELECT * 
FROM customers
LIMIT 5;
```

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/552f9deb-173e-4e9e-bf51-1c238af5b94b)

### Combining Tables Manually

Let’s return to our magazine company. Suppose we have the three tables described in the previous exercise – shown in the browser on the right (we are going to try something new!):

![image](https://github.com/Kay-Paz/Cybersecurity/assets/91631432/98ddccf1-9211-4ec0-978b-b317da908d38)  

- `orders`
- `subscriptions`
- `customers`

If we just look at the `orders` table, we can’t really tell what’s happened in each order. However, if we refer to the other tables, we can get a complete picture.

Let’s examine the order with an `order_id` of 2. It was purchased by the customer with a `customer_id` of 2.

To find out the customer’s name, we look at the `customers` table and look for the item with a `customer_id` value of 2. We can see that Customer 2’s name is ‘Jane Doe’ and that she lives at ‘456 Park Ave’.

Doing this kind of matching is called joining two tables.





***

#### FAQs

- [Are all databases relational?](https://discuss.codecademy.com/t/are-all-databases-relational/376310?_gl=1*1xpdlln*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjU5NjM1Ni43LjEuMTY5NjU5NzQxNy42MC4wLjA)
  > **No, not all databases are relational databases.** Databases can be non-relational, and this type of database is referred to as **NoSQL databases**.
  >
  > NoSQL databases are structured differently from the relational database structure:
  > - Relational:
  >   - structure tables by *the type of relations*
  >
  > - NoSQL:
  >   - keeps all the information in one place
  >       - in the form of *key-values* or *documents*
  >
  > For example, consider a database of people and their subscriptions to a newsletter.
  >
  > Using a relational database structure, we might separate the information for each person, having their id, name, and email, in one table named customers, and then another table for the subscriptions, having the newsletter name, and other information associated with the subscriptions.
  >
  > With a NoSQL database, instead of separating information in this way, we might just have a single document with the person’s information, as well as the subscription information, all in one document. As you might tell, this type of structuring might have some benefits and some cons compared to relational databases.

- [What happens if we try to create a table with an existing name?](https://discuss.codecademy.com/t/what-happens-if-we-try-to-create-a-table-with-an-existing-name/376312?_gl=1*nag98p*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjU5NjM1Ni43LjEuMTY5NjU5OTA4Ni42MC4wLjA.)
  > When you try to create a table with an already existing table name, **you will receive an error message, and no table will be modified or created**.
  >
  > Because **SQLite** *(used in the exercises)* is **case insensitive for most syntax** including names, this will apply to any casing of the table name.

- [Are there any other commonly used SQL commands?](https://discuss.codecademy.com/t/are-there-any-other-commonly-used-sql-commands/376882?_gl=1*aooy49*_ga*MTYwNDUxNDAzNy4xNjk1MjQ2NTA3*_ga_3LRZM6TM9L*MTY5NjU5OTcxMS44LjEuMTY5NjYwNDk3MS41MS4wLjA.)
  > The SQL commands covered in this lesson are probably the most common ones you will encounter or need to use when working with tables.
  >
  > Other available commands are more situational and not as commonly used. Here are some examples:  
  >
  > - `DROP TABLE`
  >   - permanently remove a table from a database
  >   - Deleting tables is generally not a frequent occurrence, so you might only use this once in a while
  > 
  > - `ANALYZE`
  >   - used to obtain statistics about a table
  >   - also not as common and you might only use them in certain situations

For a full list of all the commands provided by SQLite, which is used in the Codecademy courses, you can check out the [official SQLite documentation.](https://www.sqlite.org/docs.html) 


***

[How to remember SQL commands:](https://discuss.codecademy.com/t/how-to-remember-sql-commands/710601/3)

**SQL commands are categorized into five categories:**

1. **Data Definition Language (DDL)** - used to define the database schema. List of DDL commands:
    - `CREATE` - This command is used to create the database or its objects (like table, index, function, views, store procedure, and triggers).
    - `DROP` - This command is used to delete objects from the database.
    - `ALTER` - This is used to alter the structure of the database.
    - `TRUNCATE` - This is used to remove all records from a table, including all spaces allocated for the records are removed.
    - `COMMENT` - This is used to add comments to the data dictionary.
    - `RENAME` - This is used to rename an object existing in the database.

2. **Data Query Language (DQL)** - used for performing queries on the data within schema objects. List of DQL:
    - `SELECT` - It is used to retrieve data from the database.

3. **Data Manipulation Language (DML)** - deals with the manipulation of data present. List of DML commands:
    - `INSERT` - It is used to insert data into a table.
    - `UPDATE` - It is used to update existing data within a table.
    - `DELETE` - It is used to delete records from a database table.
    - `LOCK` - Table control concurrency.
    - `CALL` - Call a PL/SQL or JAVA subprogram.
    - `EXPLAIN PLAN` - It describes the access path to data.

4. **Data Control Language (DCL)** - deal with the rights, permissions, and other controls of the database system. List of DCL commands:
    - `GRANT` - is command gives users access privileges to the database.
    - `REVOKE` - This command withdraws the user’s access privileges given by using the GRANT command.

5. **Transaction Control Language (TCL)** - Each transaction begins with a specific task and ends when all the tasks in the group successfully complete. If any of the tasks fail, the transaction fails. The following TCL commands are used to control the execution of a
transaction:
    - `COMMIT` - Commits a Transaction
    - `ROLLBACK` - Rollbacks a transaction in case of any error occurs
    - `SAVEPOINT` - Sets a save point within a transaction.
    - `SET TRANSACTION` - Specifies characteristics for the transaction.

Source: [Geeks4Geeks.com](https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/)
