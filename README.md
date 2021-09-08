# SQL

## Querying Data

### SELECT

#### Base

Base example:

```sql
SELECT
   select_list
FROM
   table_name;
```

- `table_name` is name of table;
- `select_list` can be a column or a list of columns in a table;
- `column1, column2` - a comma (,) between two columns to separate them;
- `*` select data from all the columns of the table;

| Note that the SQL keywords are `case-insensitive`|
|:------------------------|


#### Expression

`Concatenation` of results:

```sql
SELECT
   first_name || ' ' || last_name,
   email
FROM
   customer;
```

String from first_name and last_name will concatenated;

#### Column `aliases`

```sql
SELECT
   first_name || ' ' || last_name AS full_name,
   email
FROM
   customer;
```

or `short version`

```sql
SELECT
   first_name || ' ' || last_name full_name,
   email
FROM
   customer;
```

or short version with `space between words`

```sql
SELECT
   first_name || ' ' || last_name "full name",
   email
FROM
   customer;
```

### ORDER BY columns [ASC | DESC] [NULLS FIRST | NULLS LAST]

|`ASC` option is the default|
|:--------------------------|

```sql
SELECT
   first_name, last_name
FROM
   customer
ORDER BY first_name ASC,
	last_name DESC;
```

or expression

(The `LENGTH()` function accepts a string and returns the length of that string.)

```sql
SELECT
	first_name,
	LENGTH(first_name) "first name length"
FROM
	customer
ORDER BY
	"first name length" DESC;
```

### Remove duplicate rows from a result `DISTINCT`


```sql
SELECT
   DISTINCT column1, column2
FROM
   table_name;
```

???  `DISTINCT ON`  ???

### WHERE condition

FROM => WHERE => SELECT => ORDER BY

```sql
SELECT select_list
FROM table_name
WHERE condition
ORDER BY sort_expression
```

```sql
SELECT
   city
FROM
   city
WHERE country_id = 100;
```

```sql
SELECT
	first_name,
	last_name
FROM
	customer
WHERE
	first_name IN ('Ann','Anne','Annie');
```

```sql
SELECT
	first_name,
	LENGTH(first_name) "name length"
FROM
	customer
WHERE
	first_name LIKE 'Ann%' AND
	LENGTH(first_name) BETWEEN 3 AND 5
ORDER BY
	"name length";
```


Operator |	Description
|:---:| :---|
| =   | Equal|
| >	| Greater than|
|<	| Less than|
|>=	| Greater than or equal|
|<=	| Less than or equal|
|<> or != |	Not equal|
|AND	| Logical operator AND|
|OR	| Logical operator OR|
|IN	| Return true if a value matches any value in a list|
|BETWEEN	| Return true if a value is between a range of values|
|LIKE	| Return true if a value matches a pattern|
|IS NULL	| Return true if a value is NULL|
|NOT	| Negate the result of other operators|

### LIMIT

```sql
SELECT
	film_id,
	title,
	release_year
FROM
	film
ORDER BY
	film_id
LIMIT 5;
```

`OFFSET` skip a number of rows before returning the rows

```sql
SELECT
	film_id,
	title,
	release_year
FROM
	film
ORDER BY
	film_id
LIMIT 4 OFFSET 3;
```

### FETCH

```sql
SELECT
    film_id,
    title
FROM
    film
ORDER BY
    title
OFFSET 5 ROWS
FETCH FIRST 5 ROW ONLY;
```