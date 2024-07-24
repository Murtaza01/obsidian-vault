# INSERT INTO

inserting data into our tables we use this syntax:

```sql
INSERT INTO nameOfTable(name,age)
VALUES ("theName",20);
```

1. in the first line we define what goes into our table (in this case its both name and age)
2. second we put those values in, we have to follow the same order (name first then age)
# multiple insert 

we can insert multiple values separated by commas:

```sql
INSERT INTO alpha(name,age)
VALUES ("bob",1),
("kim",20);
```

# not selecting all the columns

when we don't insert data in a specific column the default would be null

```sql
INSERT INTO alpha(name)
VALUES ("bob");
```

this will result the age column to be of type `null`

we can even put an empty row:

```sql
INSERT INTO alpha()
VALUES ();
```

we then will have tow rows with the `null` value

# showing data

to show our inserted data we use this command:

```sql
SELECT * FROM alpha;
```

# NOT NULL

we can specify if our row will be defulted to `null` or not, so that it is required and our rows won't be empty using the following command:

```sql
CREATE TABLE people(
name VARCHAR(50) NOT NULL,
age INT NOT NULL
);
```

not null serve as a required row, if we to say "this row must have a value" then we don't use not null.
# DEFAULT 

we can specify the default value of our rows (data), instead of either making them required or having them as null in this way:

```sql
CREATE TABLE mega (
 name VARCHAR(50) DEFAULT 'unknown',
 age INT DEFAULT 0
);
```

this will put those defaulted values we enter to be inside our rows when no giving values are entered, and it can be either row (meaning that we only put name and the age will be defaulted) 

# DEFAULT AND NULL

having a default value doesn't stop values from being null, we can still insert a value NULL inside our rows, the `NOT NULL` stops that behavior, the default only does its thing (having a default value)


```sql
CREATE TABLE mega (
name VARCHAR(50) NOT NULL DEFAULT 'unknown',
age INT NOT NULL DEFAULT 0
)
```


# PRIMARY KEY

we use primary key to give rows a unique identifier syntax:

```sql
CREATE TABLE nine (
id INT NOT NULL PRIMARY KEY,
name VARCHAR(50),
age INT
);
```

this will make our row (id) required and unique every time we try to insert something new in our table

there is another syntax that does the same thing:

```sql
CREATE TABLE nine (
id INT NOT NULL,
name VARCHAR(50),
age INT,
PRIMARY KEY (id)
);
```

this will say (that the id should be a primary key) but we are defining it in another line

primary keys don't have default values, so we don't need to say `NOT NULL` because it won't work if we leave it empty, this would be the syntax:

```sql
CREATE TABLE nine(
id INT PRIMARY KEY,
name VARCHAR(50),
age INT
);
```

# AUTO_INCREMENT

because we don't want to manually add ids (primary keys) we use the `auto_increment` to do exactly what the name suggest:

```sql
CREATE TABLE nine(
id INT PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(50),
age INT
);
```

this way we don't need to mention the primary key every time we want to insert something.