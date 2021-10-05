# MySQL coding style

The following document is currently work in progress.


## Common

* Language keywords MUST be written in UPPER CASE format.
* Table and column names MUST be written as they are defined in the database.
* Line length MUST not exceed 80 characters in length, everything longer than that MUST be split into multiple lines.
* To ensure better readability main keywords MUST be right aligned and MUST follow the RIVER pattern (https://www.red-gate.com/simple-talk/sql/t-sql-programming/formatting-sql-code-part-second/).

### Indentation

* Indentation MUST be performed using spaces and not tabs.
* Indent size MUST be 8 spaces.

### Separators

* Separators MUST be placed at the beginning of the line and not at the end.

Note: This is highly opiniated so we might decide later to switch to the oposite.

### Aliases

* MUST use the AS keyword.
* MUST be snake_case.

### Subqueries and other expressions

* MUST be surrounded with parenthesis.
* MUST be aliased.


## Selects

### SELECT clause

* Column name MUST be specified inline with the SELECT keyword when selecting a single column.

  Example:
  ```
  SELECT birth_date
  ```

* Column name MUST be specified on a separate line below the SELECT keyword, indented, when selecting multiple columns.

  Example:
  ```
  SELECT
          first_name
       ,  last_name
       ,  birth_date
  ```

### FROM clause

* Table name MUST be specified inline with the FROM keyword.
* Table name MUST have an alias when JOIN clauses are defined.
* From clause MUST consist of only one table. Usage of implicit JOIN statements is prohibited.

Example:
```
SELECT
        person.first_name
     ,  person.last_name
     ,  account.balance
  FROM  people AS person
 INNER
  JOIN  accounting AS account
    ON  account.person_id = person.id
```

### JOIN clause

* Inner join MUST be defined using INNER JOIN keyword, the usage of short JOIN keyword variant is prohibited.
* Left/Right outer joins MUST be defined using LEFT/RIGHT JOIN keyword, the usage of long oboslete LEFT/RIGHT OUTER JOIN keyword is prohibited.
* Joined tables MUST have an alias.

### WHERE clause, HAVING clause

* Short conditions SHOULD be specified inline.

  Example:
  
  ```
  WHERE  person.id = 5
  ```

* The AND/OR operator MUST be positioned at the beginning of the line.
* Long conditions MUST be split over multiple lines.

  Example:
  ````
  WHERE
         account.balance IS NULL
         AND person.id = 5
  ````
  
* Conditions which have complex logic must be surrounded by parenthesis.

  Example:
  ````
  SELECT  MAX(account.balance)
    FROM  people AS person
   INNER
    JOIN  acconting AS account
      ON  account.person_id = person.id
   WHERE
          (
                  YEAR(person.birth_date) >= 2000
             AND  person.first_name = "Nikola"
          )
          OR (
                  MONTH(person.birth_date) = 5
             AND  (
                         account.column_d = 1
                    AND  account.column_e IS NULL
            )
          )
  ````

### GROUP BY clause

* Column name MUST be the same as defined in the SELECT clause.
* Column name MUST be specified inline with the GROUP BY keyword when grouping by a single column.
* Column name MUST be specified separately on a new line, indented below the GROUP BY keyword, when grouping by multiple columns.
* Column separator - COMMA - MUST be positioned after the column and not before.

### ORDER BY clause

* Order direction keyword - ASC / DESC - MUST be specified inline with the column name.
* Order direction keyword MUST not be omitted.
* Column name MUST be specified inline with the ORDER BY keyword when ordered by a single column.
* Column name MUST be specified separately on a new line, indented below the ORDER BY keyword, when ordered by multiple columns.
* Column separator - COMMA - MUST be positioned after the column and not before.

### LIMIT clause

* Limit value MUST be defined inline with the LIMIT keyword.
* LIMIT clause MUST not contain an OFSET, use OFSET clause for defining one.

### OFSET clause

* Ofset value MUST be defined inline with the OFSET keyword.

## Inserts

### INSERT INTO clause

Example:
```
INSERT 
  INTO  people (
        first_name
     ,  last_name
     ,  birth_date
  )
```

### VALUES clause

Example:
```
VALUES (
        'Nikola'
     ,  'Tesla'
     ,  '1856-07-10'
)
```


## Updates

### UPDATE clause

* Table name MUST be specified inline with the UPDATE keyword when updating a single table.
* Table name MUST be specified on a separate line, indented, when updating multiple tables.

### JOIN clause

* MUST follow the same guidelines as in SELECT statement

### SET clause

* Column name MUST be specified inline after the SET keyword when updating a single column.
* Column name MUST be specified in a new row, below the SET keyword, indented, when updating multiple columns.

### WHERE clause

* MUST follow the same guidelines as in SELECT statement


Example:
```
UPDATE  accounting AS account
 INNER
  JOIN  people AS person
    ON  person.id = account.person_id
   SET  account.balance = 0
 WHERE  person.deteted = 1
```


## Deletes

### DELETE clause

* Table name MUST be ommited when deleting from a single table
* Table name MUST be specified on a new line, indented, when deleting from multiple tables.
* Table separator - COMMA - MUST be placed after the table name.

### FROM clause

* MUST follow the same guidelines as in SELECT statement

### JOIN clause

* MUST follow the same guidelines as in SELECT statement

### WHERE clause

* MUST follow the same guidelines as in SELECT statement