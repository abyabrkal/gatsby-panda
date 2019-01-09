---
title: "SQL Joins"
date: "2018-12-31"
---
#### [Part1](SQL-Begins.md)

#### [Part2](the-Aggregated-SQL.md)

#### This is Part3
---

# JOINS
## JOINING TWO OR MORE TABLES
---

## THE INNER JOIN 
It requires each row in the two joined tables to have matching column values and  creates a new result table by combining column values of two tables

```sql
SELECT * FROM left_table
INNER JOIN right_table
ON left_table.id = right_table.id
INNER JOIN another_table
ON left_table.id = another_table.id;
```

### Case when and then
You can use CASE with WHEN, THEN, ELSE, and END to define a new grouping field.

Using the populations table focused only for the year 2015, create a new field AS popsize_group to organize population size into
* 'large' (> 50 million),
* 'medium' (> 1 million), and
* 'small' groups.
Select only the country code, population size, and this new popsize_group as fields.

```sql
SELECT country_code, size,
    CASE WHEN size > 50000000 THEN 'large'
        WHEN size > 1000000 THEN 'medium'
        ELSE 'small' END
        AS popsize_group
FROM populations
WHERE year = 2015;
```



## THE LEFT and RIGHT JOINS

## OUTER JOINS

## SELF JOINS
