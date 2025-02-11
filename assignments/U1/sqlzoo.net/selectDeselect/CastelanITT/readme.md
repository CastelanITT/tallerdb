# JUAREZ CASTELAN JOSE

```sql
Problema 1:
SELECT name FROM world
  WHERE population >
     (SELECT population FROM world
      WHERE name='Russia')
```

```sql
Problema 2:
SELECT name
FROM world
WHERE continent ='Europe' AND gdp/population>
(
    SELECT gdp/population
    FROM world
    WHERE name ='United Kingdom'
)
```

```sql
Problema 3:
SELECT name, continent
FROM world
WHERE continent IN (
SELECT continent
FROM world
WHERE name IN ('Argentina', 'Australia')
)
ORDER BY name;
```

```sql
Problema 4:
SELECT name, population
FROM world
WHERE population>(
    SELECT population
    FROM world
    WHERE name='United Kingdom'
)
AND population<(
SELECT population
FROM world
WHERE name ='Germany'
)

```

```sql
Problema 5:
SELECT name, CONCAT(ROUND((population/(SELECT population FROM world WHERE name = 'Germany')) * 100), '%') AS percentage
FROM world WHERE continent = 'Europe';
```

```sql
Problema 6:
SELECT name
FROM world
WHERE gdp>ALL( SELECT gdp
FROM world
WHERE continent ='Europe' AND gdp IS NOT NULL
)
```

```sql
Problema 7:
SELECT continent, name, area
FROM world w1
WHERE area = (
    SELECT MAX(area)
    FROM world w2
    WHERE w1.continent = w2.continent
)
```

```sql
Problema 8:
SELECT continent, name
FROM world w1
WHERE name=(
SELECT MIN(name)
FROM world w2
WHERE w1.continent=w2.continent
)
```

```sql
Problema 9:
SELECT name, continent, population
FROM world
WHERE continent IN (
SELECT continent
FROM world
GROUP BY continent
HAVING MAX(population)<=25000000
)
```

```sql
Problema 10:
SELECT w1.name, w1.continent
FROM world w1
WHERE w1.population>3 * (
SELECT MAX(w2.population)
FROM world w2
WHERE w2.continent = w1.continent
 AND w2.name != w1.name
)
```
