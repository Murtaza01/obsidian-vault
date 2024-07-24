# CREATE TABLE

we use the following syntax:

```sql
CREATE TABLE cats (
	name VARCHAR(100),
	age INT
);
```

note:
1. we need to put a semicolon `;` in the end to say that's the last line
2. we need a datatype next to the data
3. usually the table name is pluralized

each data inside the table above will create a column, the stored data the we put will be the row of the table.

# SHOW TABLES

if we are in a database (using it that is) we can view the tables by using this syntax:

```sql
SHOW TABLES;
```

its pluralized !

# SHOW COLUMNS FROM name || DESC

to show extra information about our column inside a table we use this syntax:

```sql
SHOW COLUMNS FROM name;

OR

DESC name;
```

note:
1. that column here is pluralized because we are showing all the columns inside our table
2. that the name refers to the table, not the database
3. DESC stands for describe

# DROP TABLE name

to remove a table we use the following sytnax:

```sql
DROP TABLE beta;
```

