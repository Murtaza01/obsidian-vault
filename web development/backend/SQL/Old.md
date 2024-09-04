# Create Table

to create a table you need to enter the following code:

```SQL
CREATE TABLE human(
id INT NOT NULL,
name CHAR(255),
age INT,
PRIMARY KEY (id)
)
```

if you notice we use capital wording for the functions in SQL, it is the convention

**the PRIMARY KEY** is a way of creating a key that identify the column, so we use the id to identify it

we created 3 columns in the above example

# Inserting values

to insert values into our newly created table we use the code below:

```SQL
INSERT INTO human
VALUES (1,"julia",30)
/* where (id, name, age)*
```

we can insert using only specified column, in this case we have to name them:

```SQL
INSERT INTO human (id,name)
VALUES (2,"viranoca")
```

# Reading

we can show the table or a specified column of the table using the code below:

```SQL
SELECT * FROM human
/* this will show everthing in the table*/

SELECT name,age FROM human
/* this will only show name and age*/
```

we can even further it down using a condition and only show one row, for example:

```SQL
SELECT * FROM human WHERE id=2
/* this will only shows the row of id 2*/
```

# Update

to update a specific column or a specific row or item, we can use the code below:

```SQL
UPDATE human
SET birth=1998
/* if we wrote this code and run it, it would update every column with the value of birth, however if we specify with where like down below*/

UPDATE human
SET birth=1998
WHERE id=2
```

# Alter table

to add a new column, we use the alter table key word, followed by the column name, example:

```SQL
ALTER TABLE human
ADD fav-activity VARCHAR(255)
/* ADD columnName dataType*/
```

to *Remove* columns we use the code below:

```SQL
ALTER TABLE human
DROP COLUMN birth
```

if we want a more specific way of deleting, we use the delete keyword followed by which thing to delete, see the code below:

```SQL
DELETE FROM human
WHERE id=2
```

this will delete an entire row

# Foreign Key

a foreign key is a way to add relationship between our Tables, it is defined when we first add a table, see the example below:

```SQL
CREATE TABLE person (
  id INT not NULL,
  job VARCHAR(255),
  workTime INT,
  human_id INT,
  PRIMARY KEY (id),
  FOREIGN KEY (human_id) REFERENCES human (id)
  )
```

where the Foreign key is what column we want to use for the relation, and the reference is the id in our other table

we can then use the key word JOIN to join multiple Tables together, see the code below:

```SQL
SELECT human.name, human.age, person.job 
FROM person
INNER JOIN human ON person.human_id = human.id
```

we are simply merging to Tables together into a new row