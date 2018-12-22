# the SQL 

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

#### WHERE AND OR
```sql
SELECT title FROM films WHERE release_year > 1994 AND release_year < 2000;

SELECT title FROM films 
WHERE (release_year = 1994 OR release_year = 1995)
AND (certification = 'PG' OR certification = 'R');
```

#### BETWEEN (and it's inclusive)
```sql
SELECT title FROM films
WHERE release_year BETWEEN 1994 AND 2000; 
```

#### MULTIPLE OR conditions with WHERE IN
```sql
SELECT title FROM films
WHERE release_year IN (2000, 2005, 2010, 2015, 2020);

SELECT title FROM films WHERE certification IS NULL;
```

#### LIKE / NOT LIKE
`LIKE` operator can be used in a `WHERE` clause to search for a pattern in a column. To accomplish this, you use something called a *wildcard*(%) as a placeholder for some other values.

```sql
SELECT title FROM films WHERE title LIKE 'Data%';
```


## AGGREGATE
---

Aggregate functions to perform some calculation on the data in a database.

#### AVG(), SUM(), MIN(), MAX()

Total budget of movies made in the year 2010 or later

```sql
SELECT SUM(budget) FROM films
WHERE release_year >= 2010;
```

#### ALIASING - AS

```sql
SELECT MAX(budget) AS max_budget,
       MAX(duration) AS max_duration
FROM films;
```


Average duration in hours for all films, aliased as `avg_duration_hours`.
```sql
SELECT  avg(duration)/60.0 as avg_duration_hours from films;
```

Get the percentage of `people` who are no longer alive. 
```sql
select COUNT(deathdate) * 100.0 / COUNT(*) AS percentage_dead from people;
```