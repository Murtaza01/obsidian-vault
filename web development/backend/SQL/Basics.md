to select a database:

```sql
USE <name>;
```

or by double clicking inside the workbench 

to show the current used database:

```sql
SELECT DATABASE();
```

to show our databases:

```sql
SHOW DATABASES;
```

pluralized !

# notes

database contains multiples tables, tables are the things which are going to hold our data, columns are the data that we are going to put inside our tables, they need types (string or int).


# using single quote  

its best to use single quotation instead of the two, to avoid problems, because most SQL management system don't allow double quotes 

we can escape single quotes using the \ (back slash)

```sql
INSERT INTO shops (name) VALUES ('baber\'s shop')
```

