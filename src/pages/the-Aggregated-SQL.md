---
title: "The Aggregated SQL"
date: "2018-12-24"
---
#### [Part1](SQL-Begins.md)
#### This is Part2
---

## AGGREGATE
---

Aggregate functions to perform some calculation on the data in a database.

#### AVG(), SUM(), COUNT(), MIN(), MAX()
SELECT SUM returns the sum of the data values.
SELECT AVG returns the average of the data values.
SELECT COUNT returns a count of the number of data values.
SELECT MIN returns the minimum value for a column.
SELECT MAX returns the maximum value for a column.


Total budget of movies made in the year 2010 or later
```sql
SELECT SUM(budget) FROM films
WHERE release_year >= 2010;
```

#### ALIASING - AS
Creates an alias of a table or column.

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


#### ORDER BY
Sorts the returned data from a query in ascending or descending order based on a specified criteria or column value.

```sql
SELECT title FROM films ORDER BY release_year DESC;

select name, birthdate from people order by name, birthdate
```

#### GROUP BY
Aggregates rows that share common criteria (e.g. a column value) and will return all of the unique entries found for such criteria. Allows you to group a result by one or more columns.

```sql
select release_year, max(budget) from films group by release_year, title
```

Get the country, release year, and lowest amount grossed per release year per country. Order your results by country and release year
```sql
select country, release_year, min(gross) from films 
group by release_year, country 
order by country, release_year
```

#### HAVING 
HAVING filters records that work on summarized GROUP BY results. HAVING applies to summarized group records, whereas WHERE applies to individual records. The HAVING clause was added to SQL because the WHERE keyword could not be used with aggregate functions.

Average budget and average gross earnings for films in each year after 1990, if the average budget is greater than $60 million
```sql
select  release_year, 
        avg(budget) as avg_budget,
        avg(gross) as avg_gross from films 
where release_year > 1990 
group by release_year
having avg(budget) > 60000000
order by avg_gross desc
```

Get the country, average budget, and average gross take of countries that have made more than 10 films. Order the result by country name, and limit the number of results displayed to 5. You should alias the averages as avg_budget and avg_gross respectively.
```sql
-- select country, average budget, average gross
select country, avg(budget) as avg_budget, avg(gross) as avg_gross
-- from the films table
from films
-- group by country 
group by country
-- where the country has more than 10 titles
having count(title) > 10
-- order by country
order by country
-- limit to only show 5 results
limit 5
```

### JOIN
Joining two different tables based on a commmon field is for another day.
[SQL Begins](SQL-Begins.md) 
[SQL Joins: Part 3...]()