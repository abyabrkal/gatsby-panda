---
title: "SQL Begins"
date: "2018-12-22"
---
#### This is Part1
#### [Part2](the-Aggregated-SQL.md)
---
*Story:* This SQL journey was noted while taking free [SQL lessons from DataCamp](https://www.datacamp.com/courses/intro-to-sql-for-data-science). So, you may see datas familiar from that course and used it for my easy recollection. 



Consider the table 'films'

| id   | title                | release_year | country | duration | language | certification | gross   | budget  |
| ---- | -------------------- | ------------ | ------- | -------- | -------- | ------------- | ------- | ------- |
| 1    | The Great Escape     | 1963         | USA     | 172      | English  | Approved      | null    | 4000000 |
| 2    | The Broadway Melody  | 1929         | USA     | 100      | English  | Passed        | 2808000 | 379000  |
| 3    | A Fistful of Dollars | 1964         | Italy   | 99       | Italian  | R             | 3500000 | 200000  |
| 4    | Metropolis           | 1927         | Germany | 145      | German   | Not Rated     | 26435   | 6000000 |

## SELECTION
---

Select all from films and limit the display to 3 rows
```sql
SELECT * FROM films LIMIT 3;
```

Getting the language represented in films without repeats
```sql
SELECT DISTINCT language FROM films;
```

Count the number of rows 
```sql
SELECT COUNT(*) FROM films;

SELECT COUNT(title) FROM people;
```

## FILTER
---


#### Basic Filtering conditions

- `=` equal 
- `<>` not equal
- `<` less than
- `>` greater than
- `<=` less than or equal to
- `>=` greater than or equal to

Select all from films for all movies released after 1980 (not including 1980)
```sql
SELECT * FROM films WHERE release_year > 1980;

SELECT title FROM films WHERE title = 'Metropolis';
```

#### WHERE AND-OR-NOT

```sql
SELECT title FROM films WHERE release_year > 1994 AND release_year < 2000;

SELECT title FROM films 
WHERE (release_year = 1994 OR release_year = 1995)
AND (certification = 'PG' OR certification = 'R');
```

#### BETWEEN (and it's inclusive)
WHERE BETWEEN returns values that fall within a given range.

```sql
SELECT title FROM films
WHERE release_year BETWEEN 1994 AND 2000; 
```

#### MULTIPLE OR conditions with WHERE IN
WHERE IN returns values that matches values in a list or subquery (Shorthand for multiple OR conditions).

```sql
SELECT title FROM films
WHERE release_year IN (2000, 2005, 2010, 2015, 2020);

SELECT title FROM films WHERE certification IS NULL;
```

#### LIKE (% and _)
`LIKE` operator can be used in a `WHERE` clause to search for a pattern in a column. It supports two wildcard match options: % and _

```sql
SELECT title FROM films WHERE title LIKE 'Data%';
```

#### SELECT DISTINCT
Returns only distinct (different) values and eliminates duplicate records from the results

```sql
SELECT COUNT (DISTINCT country) FROM films;
```

### AGGREGATES
This one needs a separate page for itself. [SQL Page-2: The Aggregated SQL](the-Aggregated-SQL.md)
