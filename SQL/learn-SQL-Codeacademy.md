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

### Manipulation

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

#### Statements

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

#### CREATE

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

#### INSERT

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

##### Inserting Multiple Rows:

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

#### SELECT

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

#### ALTER

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

#### UPDATE

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

#### DELETE

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

#### Constraints

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

### Review

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
