# The Aggregated SQL
### Part 2

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


#### ORDER BY

```sql
SELECT title FROM films ORDER BY release_year DESC;

select name, birthdate from people order by name, birthdate
```

#### ORDER BY
Allows you to group a result by one or more columns

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