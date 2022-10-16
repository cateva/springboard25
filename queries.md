Make sure you download the starter code and run the following:

```sh
  psql < movies.sql
  psql movies_db
```

In markdown, you can place a code block inside of three backticks (```) followed by the syntax highlighting you want, for example

\```sql

SELECT \* FROM movies;

\```

Using the `movies_db` database, write the correct SQL queries for each of these tasks:

1.  The title of every movie.
```sql

SELECT \title FROM movies;

```

2.  All information on the G-rated movies.
```sql

SELECT \* FROM movies WHERE rating = 'G';

```

3.  The title and release year of every movie, ordered with the oldest movie first.
```sql

SELECT \* FROM movies;

```

4.  All information on the 5 longest movies.
```sql

SELECT \* FROM movies
    ORDER BY runtime DESC
    LIMIT 5;

```

5.  A query that returns the columns of `rating` and `total`, tabulating the
    total number of G, PG, PG-13, and R-rated movies.
```sql

SELECT \SUM(title) 
    FROM movies
    GROUP BY rating
    ORDER BY rating;

```

6.  A table with columns of `release_year` and `average_runtime`,
    tabulating the average runtime by year for every movie in the database. The data should be in reverse chronological order (i.e. the most recent year should be first).

```sql

SELECT \release_year,  AVG(runtime)
    FROM movies
    ORDER BY release_year DESC;

```

7.  The movie title and studio name for every movie in the database.

```sql

SELECT \movies.title, studios.name
    FROM movies
    JOIN studios
    ON movies.studio_id = studios.id;

```

8.  The star first name, star last name, and movie title for every matching movie and star pair in the database.

```sql

SELECT \stars.first_name, stars.last_name, movies.title
    FROM movies
    JOIN roles
    ON movies.id = roles.movie_id
    JOIN stars
    ON stars.id = roles.star_id;

```

9.  The first and last names of every star who has been in a G-rated movie. The first and last name should appear only once for each star, even if they are in several G-rated movies. *IMPORTANT NOTE*: it's possible that there can be two *different* actors with the same name, so make sure your solution accounts for that.

```sql

SELECT \stars.first_name, stars.last_name
    FROM movies
    JOIN roles
    ON movies.id = roles.movie_id
    RIGHT JOIN stars
    ON stars.id = roles.star_id
    WHERE rating = 'G';

```

10. The first and last names of every star along with the number of movies they have been in, in descending order by the number of movies. (Similar to #9, make sure
that two different actors with the same name are considered separately).

```sql

SELECT stars.first_name, stars.last_name, COUNT(movies.title) AS total
    FROM movies
    JOIN roles
    ON movies.id = roles.movie_id
    RIGHT JOIN stars
    ON stars.id = roles.star_id
    GROUP BY stars.first_name, stars.last_name
    ORDER BY total DESC;

```

### The rest of these are bonuses

11. The title of every movie along with the number of stars in that movie, in descending order by the number of stars.

```sql

SELECT movies.title, COUNT(stars.id) AS total
    FROM stars
    JOIN roles
    ON stars.id = roles.star_id
    JOIN movies
    ON movies.id = roles.movie_id
    GROUP BY movies.title
    ORDER BY total DESC;
```

12. The first name, last name, and average runtime of the five stars whose movies have the longest average.

```sql

SELECT stars.first_name, stars.last_name, AVG(movies.runtime) AS x
    FROM stars
    JOIN roles
    ON stars.id = roles.star_id
    JOIN movies
    ON movies.id = roles.movie_id
    GROUP BY stars.first_name, stars.last_name
    ORDER BY x DESC LIMIT 5;

```

13. The first name, last name, and average runtime of the five stars whose movies have the longest average, among stars who have more than one movie in the database.

```sql

SELECT stars.first_name, stars.last_name, AVG(movies.runtime) AS x, COUNT(movies.id) AS y
    FROM stars
    JOIN roles
    ON stars.id = roles.star_id
    WHERE y > 1
    JOIN movies
    ON movies.id = roles.movie_id
    GROUP BY stars.first_name, stars.last_name
    ORDER BY x DESC LIMIT 5; 

```


14. The titles of all movies that don't feature any stars in our database.

```sql

SELECT movies.title
    FROM stars
    FULL JOIN roles
    ON stars.id = roles.star_id
    FULL JOIN movies
    ON movies.id = roles.movie_id
    WHERE roles.star_id = NULL;
    
```

15. The first and last names of all stars that don't appear in any movies in our database.

```sql

SELECT stars.first_name, stars.last_name, movies.title
    FROM stars
    FULL JOIN roles
    ON stars.id = roles.star_id
    FULL JOIN movies
    ON movies.id = roles.movie_id
    WHERE roles.movie_id = NULL;

```

16. The first names, last names, and titles corresponding to every
    role in the database, along with every movie title that doesn't have a star, and the first and last names of every star not in a movie.