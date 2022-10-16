### Conceptual Exercise

Answer the following questions below:

- What is PostgreSQL?
PostgreSQL is an advanced, enterprise-class, and open-source relational database system. PostgreSQL supports both SQL (relational) and JSON (non-relational) querying. PostgreSQL is a highly stable database backed by more than 20 years of development by the open-source community. PostgreSQL is used as a primary database for many web applications as well as mobile and analytics applications.

- What is the difference between SQL and PostgreSQL?
SQL server is a database management system which is mainly used for e-commerce and providing different data warehousing solutions. PostgreSQL is an advanced version of SQL which provides support to different functions of SQL like foreign keys, subqueries, triggers, and different user-defined types and functions.

- In `psql`, how do you connect to a database?
$ createdb my_database_name

- What is the difference between `HAVING` and `WHERE`?
HAVING Clause is used to filter the records from the groups based on the given condition in the HAVING Clause. Those groups who will satisfy the given condition will appear in the final result. HAVING Clause can only be used 
with SELECT statement. 

WHERE Clause is used to filter the records from the table or used while joining more than one table.Only those records will be extracted who are satisfying the specified condition in WHERE clause. It can be used with SELECT, UPDATE, DELETE statements. 

- What is the difference between an `INNER` and `OUTER` join?
The major difference between inner and outer joins is that inner joins result in the intersection of two tables, whereas outer joins result in the union of two tables.

- What is the difference between a `LEFT OUTER` and `RIGHT OUTER` join?
Left outer join includes the unmatched rows from the table which is on the left of the join clause whereas a Right outer join includes the unmatched rows from the table which is on the right of the join clause.

- What is an ORM? What do they do?
An object-relational mapper (ORM) is a code library that automates the transfer of data stored in relational database tables into objects that are more commonly used in application code.

- What are some differences between making HTTP requests using AJAX and from the server side using a library like `requests`?

When the browser makes a regular request as in window.location.href = "index.html", it clears the current window and loads the server response into the window.

With an ajax request, the current window/document is unaffected and javascript code can examine the results of the request and do what it wants to with those results (insert HTML dynamically into the page, parse JSON and use it the page logic, parse XML, etc...).

The server doesn't do anything different - it's just in how the client treats the response from the two requests.

- What is CSRF? What is the purpose of the CSRF token?
Cross-Site Request Forgery (CSRF) is a type of attack that occurs when a malicious web site, email, blog, instant message, or program causes a user's web browser to perform an unwanted action on a trusted site when the user is authenticated.

A CSRF token is a secure random token (e.g., synchronizer token or challenge token) that is used to prevent CSRF attacks. The token needs to be unique per user session and should be of large random value to make it difficult to guess. A CSRF secure application assigns a unique CSRF token for every user session.

- What is the purpose of `form.hidden_tag()`?
A template argument generates a hidden field that includes a token that is used to protect the form against CSRF attacks. All you need to do to have the form protected is include this hidden field and have the SECRET_KEY variable defined in the Flask configuration.