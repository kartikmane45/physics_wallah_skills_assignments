#QUES1. Create a table called employees with the following structure?
#: emp_id (integer, should not be NULL and should be a primary key)Q
#: emp_name (text, should not be NULL)Q
#: age (integer, should have a check constraint to ensure the age is at least 18)Q
#: email (text, should be unique for each employee)Q
#: salary (decimal, with a default value of 30,000).
#Write the SQL query to create the above table with all constraints.

use employees;
create table employee(
EMPID INT PRIMARY KEY,
EMPNAME VARCHAR(50)NOT NULL,
AGE INT CHECK(AGE <= 18),
EMAIL VARCHAR(50) UNIQUE,
SALARY float DEFAULT(30000));

#QUES2 - . Explain the purpose of constraints and how they help maintain data integrity in a database. Provide
# examples of common types of constraints ?

#ANSWER - SQL constraints are used to specify rules for data in a table like
#1. NOT NULL - COLUMNS CANNOT HAVE A NULL VALUES
#2. UNIQUE- ALL VALUES IN A COLUMN ARE DIFFERENT
#3. PRIMARY KEY - UNIQUE COLUMN AND NOT NULL BUT USED FOR ONLY ONE
#4. FOREIGN KEY- PREVENT ACTIONS THAT WOULD DESTROY LINKS BETWEEN TABLES.
#5. DEFAULT - SETS THE DEFAULT VALUE OF A COLUMN / CHECK - IT CAN LIMIT THE VALUES ALLOWED IN A COLUMN.

#QUES3- Why would you apply the NOT NULL constraint to a column? Can a primary key contain NULL values? Justify your answer.

#ANSWER- We apply not null constraint to a column because it should be not null and a primary key can not contain a null values.

#QUES-4 Explain the steps and SQL commands used to add or remove constraints on an existing table. Provide an
#example for both adding and removing a constraint

#In SQL, constraints are used to define rules or conditions on data columns in a table. You can add or remove constraints from an existing table using the following SQL commands and steps.
#example of adding constraint to a existing table
ALTER TABLE employee
MODIFY COLUMN EMPID INT NOT NULL;

#Removing constraint
ALTER TABLE employee
MODIFY COLUMN EMPID INT;

#Ques -5  Explain the consequences of attempting to insert, update, or delete data in a way that violates constraints.
#provide example of an error message that might occur when violating a constraint ?

#Insertion Failures: If you try to insert a row that violates a constraint, the database will reject the operation and return an error message.
#Update Failures: If you attempt to modify data in a way that would violate a constraint (e.g., changing a value in a foreign key column to one that doesn't exist in the referenced table), the update will fail.
#Deletion Failures: If you attempt to delete a record that is being referenced by a foreign key in another table, the database will prevent the deletion to maintain referential integrity.
#Example of an error message:-
#ERROR: duplicate key value violates unique constraint "table_pkey"
#DETAIL: Key (id)=(1) already exists.

#Ques-6 You created a products table without constraints as follows:
CREATE TABLE products (
    product_id INT,
    product_name VARCHAR(50),
    price DECIMAL(10, 2));
 
#Now, you realise that?: The product_id should be a primary keyQ: The price should have a default value of 50.00
ALTER TABLE products
ADD CONSTRAINT pk_product_id PRIMARY KEY (product_id);

ALTER TABLE products
ALTER COLUMN price SET DEFAULT 50.00;

#QUES-7 You have two tables:
create table Students(
     studentId INT PRIMARY KEY,
     STUDENTNAME VARCHAR(50),
     CLASSID INT);
INSERT INTO Students
(studentID , STUDENTNAME , CLASSID)
VALUES
(1, 'ALICE',101),
(2, 'BOB', 102),
(3, 'CHARLIE',101);

CREATE TABLE CLASSES(
    CLASSID INT,
    CLASSNAME VARCHAR(50));
INSERT INTO CLASSES(CLASSID , CLASSNAME)
VALUES
(101 , 'MATH'),
(102 , 'SCIENCE'),
(103 , 'HISTORY');

#Write a query to fetch the student_name and class_name for each student using an INNER JOIN.
SELECT Students.studentID, Students.STUDENTNAME, Classes.CLASSNAME
FROM Students
INNER JOIN Classes
    ON Students.CLASSID = Classes.CLASSID;
    
#QUES-8 Consider the following three tables:
CREATE TABLE ORDERS(
ORDERID INT ,
ORDERDATE DATE,
CUSTID INT);
INSERT INTO ORDERS (ORDERID, ORDERDATE, CUSTID)
VALUES
    (1, '2024-01-01', 101),
    (2, '2024-01-03', 102);

CREATE TABLE CUSTOMERS(
CUSTID INT,
CUSTNAME VARCHAR(50));
INSERT INTO CUSTOMERS (CUSTID , CUSTNAME)
VALUES
(101 , "ALICE"),
(102 , "BOB");

CREATE TABLE PRODUCT(
PRODUCTID INT,
PRODUCTNAME VARCHAR(50),
ORDERID INT);

INSERT INTO PRODUCT (PRODUCTID , PRODUCTNAME , ORDERID)
VALUES
(1 , "LAPTOP" , 1),
(2 , "MOBILE" , NULL);

# Write a query that shows all order_id, customer_name, and product_name, ensuring that all products are listed even if they are not associated with an order 
SELECT ORDERS.ORDERID, CUSTOMERS.CUSTID, PRODUCT.PRODUCTID
FROM ORDERS
INNER JOIN CUSTOMERS ON ORDERS.CUSTID = CUSTOMERS.CUSTID
INNER JOIN PRODUCT ON ORDERS.ORDERID = PRODUCT.ORDERID
LIMIT 0, 1000;

#QUES-9 Given the following tables:
CREATE TABLE SALES(
SALEID INT PRIMARY KEY,
PRODUCTID INT ,
AMOUNT INT);

INSERT INTO SALES(SALEID , PRODUCTID , AMOUNT)
VALUES
(1 , 101 , 500),
(2 , 102 , 300),
(3, 101 , 700);

CREATE TABLE PRODUCTT(
PRODUCTID INT,
PRODUCTNAME VARCHAR(50));
INSERT INTO PRODUCTT(PRODUCTID , PRODUCTNAME)
VALUES
(101 , "LAPTOP"),
(102 , "PHONE");

#Write a query to find the total sales amount for each product using an INNER JOIN and the SUM() function.
SELECT PRODUCTT.PRODUCTNAME, SUM(SALES.AMOUNT) AS TOTAL_SALES_AMOUNT
FROM SALES
INNER JOIN PRODUCTT ON SALES.PRODUCTID = PRODUCTT.PRODUCTID
GROUP BY PRODUCTT.PRODUCTNAME;

#QUES-10 You are given three tables:
CREATE TABLE OrderDetails(
OrderID INT,
PRODUCTID INT,
QUANTITY INT);

INSERT INTO OrderDetails(OrderID, PRODUCTID , QUANTITY)
VALUES
(1 , 101 , 2),
(2 , 102 , 1),
(3 , 101 , 3);
select * from customers;

#Write a query to display the order_id, customer_name, and the quantity of products ordered by each customer using an INNER JOIN between all three tables.
select orderdetails.OrderID, customers.CUSTNAME , product.PRODUCTID;

##SQL COMMANDS
# 1-Identify the primary keys and foreign keys in maven movies db. Discuss the differences
use mavenmovies;
# Primary key
SELECT 
    table_name, 
    column_name
FROM 
    information_schema.key_column_usage
WHERE 
    table_schema = 'mavenmovies' 
    AND constraint_name = 'PRIMARY';

# Foreign key
SELECT 
    table_name, 
    column_name, 
    constraint_name, 
    referenced_table_name, 
    referenced_column_name
FROM 
    information_schema.key_column_usage
WHERE 
    table_schema = 'mavenmovies' 
    AND referenced_table_name IS NOT NULL;


# 2- List all details of actors
select * from actor;

#3- List all customer information from DB.
select * from customer;

#4- List different countries
select country from country;

#5- Display all active customers.
select * from customer
where active = 1;

#6 -List of all rental IDs for customer with ID 1.
select rental_id , customer_id from rental
where customer_id = 1;

#7 - Display all the films whose rental duration is greater than 5 .
select * from film
where rental_duration > 5;

#8-  List the total number of films whose replacement cost is greater than $15 and less than $20.
select * from film 
where replacement_cost > 15 and replacement_cost< 20;

# 9 - Display the count of unique first names of actors.
select first_name ,count(first_name) as count from actor
group by first_name ;

# 10- Display the first 10 records from the customer table .
select * from customer
limit 10;

#11 - Display the first 3 records from the customer table whose first name starts with ‘b’.
select * from customer
where first_name like 'b%'
limit 3;

#12 -Display the names of the first 5 movies which are rated as ‘G’.
select * from film
where rating = 'G'
limit 5;

#13-Find all customers whose first name starts with "a".
select * from customer
where first_name like "a%";

#14- Find all customers whose first name ends with "a".
select * from customer
where first_name like "%a";

#15- Display the list of first 4 cities which start and end with ‘a’ .
select * from city
where city like 'a%a'
limit 4;

#16- Find all customers whose first name have "NI" in any position.
select * from customer
where first_name like '%NI%';

#17- Find all customers whose first name have "r" in the second position .
select * from customer
where first_name like '_r%' ;

#18 - Find all customers whose first name starts with "a" and are at least 5 characters in length.
select * from customer
where first_name like '_r___%' ;

#19- Find all customers whose first name starts with "a" and ends with "o".
select * from customer
where first_name like 'a%o' ;

#20 - Get the films with pg and pg-13 rating using IN operator.
select * from film
where rating IN ('PG','PG-13');

#21 - Get the films with length between 50 to 100 using between operator.
select title , length from film
where length between 50 and 100;

#22 - Get the top 50 actors using limit operator.
select * from actor
limit 50;

#23 - Get the distinct film ids from inventory table.
select DISTINCT film_id from inventory;

#FUNCTIONS >> basic aggregate functions
#Question 1: Retrieve the total number of rentals made in the Sakila database.
select count(*) as totalrental
from rental;

#QUES-2 Find the average rental duration (in days) of movies rented from the Sakila database.
select title , 
AVG(RENTAL_DURATION) from film
group by title;

#QUES-3 Display the first name and last name of customers in uppercase.
select UPPER(first_name ) ,upper(last_name)
from customer;

#QUES-4 Extract the month from the rental date and display it alongside the rental ID.
select month(rental_date)as months, rental_id from rental;

#QUES-5 Retrieve the count of rentals for each customer (display customer ID and the count of rentals).
SELECT COUNT(staff_id) as count , customer_id FROM RENTAL
group by customer_id;

#QUES-6 Find the total revenue generated by each store
SELECT 
    s.store_id,
    SUM(p.amount) AS total_revenue
FROM 
    store s
JOIN 
    customer c ON s.store_id = c.store_id
JOIN 
    payment p ON c.customer_id = p.customer_id
GROUP BY 
    s.store_id;

#QUES-7  Determine the total number of rentals for each category of movies.

SELECT c.name AS category, COUNT(r.rental_id) AS total_rentals
FROM rental r
JOIN inventory i ON r.inventory_id = i.inventory_id
JOIN film f ON i.film_id = f.film_id
JOIN film_category fc ON f.film_id = fc.film_id
JOIN category c ON fc.category_id = c.category_id
GROUP BY c.name;

#QUES-8 Find the average rental rate of movies in each language
select avg(rental_rate) AS AVERAGE , language_id from film
group by language_id;

##JOINS
# Questions 9 -Display the title of the movie, customer s first name, and last name who rented it.

  SELECT film.title, customer.first_name, customer.last_name
FROM rental
JOIN customer 
  ON rental.customer_id = customer.customer_id
JOIN inventory
  ON rental.inventory_id = inventory.inventory_id
JOIN film
  ON inventory.film_id = film.film_id;
  
#QUES-10 Retrieve the names of all actors who have appeared in the film "Gone with the Wind."
# THERE IS NO TITLE CALLED GONE WITH THE GONE IN FILM TABLE

#QUES-11 Retrieve the customer names along with the total amount they've spent on rentals.
SELECT customer.first_name, payment.amount
FROM customer
JOIN payment
  ON customer.customer_id = payment.customer_id;
  
#QUES-12 List the titles of movies rented by each customer in a particular city (e.g., 'London').

SELECT customer.first_name, customer.last_name, film.title
FROM customer
JOIN address
  ON customer.address_id = address.address_id
JOIN rental
  ON customer.customer_id = rental.customer_id
JOIN inventory
  ON rental.inventory_id = inventory.inventory_id
JOIN film
  ON inventory.film_id = film.film_id
WHERE address.district = 'London';

#QUES-13 Display the top 5 rented movies along with the number of times they've been rented.
SELECT film.title, COUNT(rental.rental_id) AS rental_count
FROM rental
JOIN inventory
  ON rental.inventory_id = inventory.inventory_id
JOIN film
  ON inventory.film_id = film.film_id
GROUP BY film.film_id
ORDER BY rental_count DESC
LIMIT 5;

#QUES-14 Determine the customers who have rented movies from both stores (store ID 1 and store ID 2).

SELECT customer.first_name, customer.last_name
FROM rental
JOIN customer
  ON rental.customer_id = customer.customer_id
JOIN inventory
  ON rental.inventory_id = inventory.inventory_id
JOIN store
  ON inventory.store_id = store.store_id
WHERE store.store_id IN (1, 2)
GROUP BY customer.customer_id
HAVING COUNT(DISTINCT store.store_id) = 2;

##WINDOWS FUNCTION
#QUES-1  Rank the customers based on the total amount they've spent on rentals.
SELECT customer.first_name, customer.last_name, SUM(payment.amount) AS total_spent
FROM customer
JOIN payment
  ON customer.customer_id = payment.customer_id
GROUP BY customer.customer_id
ORDER BY total_spent DESC;

#QUES-2 Calculate the cumulative revenue generated by each film over time?
SELECT 
    film.title,
    payment.payment_date,
    SUM(payment.amount) OVER (PARTITION BY film.film_id ORDER BY payment.payment_date) AS cumulative_revenue
FROM payment
JOIN rental
    ON payment.rental_id = rental.rental_id
JOIN inventory
    ON rental.inventory_id = inventory.inventory_id
JOIN film
    ON inventory.film_id = film.film_id
ORDER BY film.film_id, payment.payment_date;

#QUES-3  Determine the average rental duration for each film, considering films with similar lengths.
SELECT 
    FLOOR(film.length / 10) * 10 AS length_bin,  -- Grouping by 10-minute intervals
    AVG(film.rental_duration) AS avg_rental_duration
FROM rental
JOIN inventory
    ON rental.inventory_id = inventory.inventory_id
JOIN film
    ON inventory.film_id = film.film_id
GROUP BY length_bin
ORDER BY length_bin;

#QUES-4  Identify the top 3 films in each category based on their rental count

SELECT 
    fc.film_id, 
    f.title, 
    c.name AS category_name, 
    COUNT(r.rental_id) AS rental_count
FROM rental r
JOIN inventory i ON r.inventory_id = i.inventory_id
JOIN film f ON i.film_id = f.film_id
JOIN film_category fc ON f.film_id = fc.film_id
JOIN category c ON fc.category_id = c.category_id
GROUP BY fc.film_id, c.category_id
ORDER BY category_name, rental_count DESC
LIMIT 3;

#QUES-5 Calculate the difference in rental counts between each customer's total rentals and the average rentals across all customers.

SELECT 
    customer.customer_id,
    customer.first_name,
    customer.last_name,
    total_rentals,
    total_rentals - avg_rentals AS rental_diff
FROM (
    SELECT 
        customer_id,
        COUNT(rental_id) AS total_rentals
    FROM rental
    GROUP BY customer_id
) AS customer_rentals
JOIN customer 
    ON customer_rentals.customer_id = customer.customer_id
JOIN (
    SELECT 
        AVG(rental_count) AS avg_rentals
    FROM (
        SELECT COUNT(rental_id) AS rental_count
        FROM rental
        GROUP BY customer_id
    ) AS rentals_per_customer
) AS avg_rentals_subquery
ON 1 = 1
ORDER BY rental_diff DESC;


#QUES-6. Find the monthly revenue trend for the entire rental store over time.
SELECT 
    YEAR(payment_date) AS year,
    MONTH(payment_date) AS month,
    SUM(payment.amount) AS monthly_revenue
FROM payment
GROUP BY YEAR(payment_date), MONTH(payment_date)
ORDER BY year, month;

#QUES-7. Identify the customers whose total spending on rentals falls within the top 20% of all customers.
select * from customer;

WITH CustomerSpending AS (
    SELECT 
        customer_id, 
        SUM(amount) AS total_spending
    FROM payment
    GROUP BY customer_id
),
RankedCustomers AS (
    SELECT 
        customer_id,
        total_spending,
        PERCENT_RANK() OVER (ORDER BY total_spending DESC) AS spending_percentile
    FROM CustomerSpending
)
SELECT 
    customer_id,
    total_spending
FROM RankedCustomers
WHERE spending_percentile >= 0.80
ORDER BY total_spending DESC;

#QUES-8 Calculate the running total of rentals per category, ordered by rental count.
WITH CategoryRentalCounts AS (
    SELECT 
        c.name AS category_name,
        COUNT(r.rental_id) AS rental_count
    FROM rental r
    JOIN inventory i ON r.inventory_id = i.inventory_id
    JOIN film f ON i.film_id = f.film_id
    JOIN film_category fc ON f.film_id = fc.film_id
    JOIN category c ON fc.category_id = c.category_id
    GROUP BY c.category_id
)
SELECT 
    category_name,
    rental_count,
    SUM(rental_count) OVER (ORDER BY rental_count DESC) AS running_total
FROM CategoryRentalCounts
ORDER BY rental_count DESC;

#QUES-9. Find the films that have been rented less than the average rental count for their respective categories.
WITH FilmRentalCounts AS (
    SELECT 
        f.film_id,
        f.title,
        c.name AS category_name,
        COUNT(r.rental_id) AS rental_count
    FROM rental r
    JOIN inventory i ON r.inventory_id = i.inventory_id
    JOIN film f ON i.film_id = f.film_id
    JOIN film_category fc ON f.film_id = fc.film_id
    JOIN category c ON fc.category_id = c.category_id
    GROUP BY f.film_id, c.category_id
),
CategoryAverageRental AS (
    SELECT 
        category_name,
        AVG(rental_count) AS avg_rental_count
    FROM FilmRentalCounts
    GROUP BY category_name
)
SELECT 
    fr.film_id,
    fr.title,
    fr.category_name,
    fr.rental_count,
    ca.avg_rental_count
FROM FilmRentalCounts fr
JOIN CategoryAverageRental ca
    ON fr.category_name = ca.category_name
WHERE fr.rental_count < ca.avg_rental_count
ORDER BY fr.category_name, fr.rental_count;

#QUES-10 Identify the top 5 months with the highest revenue and display the revenue generated in each month.
SELECT 
    YEAR(payment_date) AS year,
    MONTH(payment_date) AS month,
    SUM(amount) AS total_revenue
FROM payment
GROUP BY YEAR(payment_date), MONTH(payment_date)
ORDER BY total_revenue DESC
LIMIT 5;

## NORMALIZATION & CTE
#1. First Normal Form (1NF):
# a. Identify a table in the Sakila database that violates 1NF. Explain how you would normalize it to achieve 1NF
use mavenmovies;
select * from actor;
#actor table is already a 1nf table

#QUES-2  Second Normal Form (2NF):
#a. Choose a table in Sakila and describe how you would determine whether it is in 2NF. If it violates 2NF, explain the steps to normalize it.

#Second Normal Form (2NF) requires that a table first be in 1NF and that all non-key columns depend on the whole primary key, not just part of it (in the case of a composite key).
#In the example of the film_actor table, it was already in 2NF, as no partial dependencies existed.


#QUES-3 3. Third Normal Form (3NF):
#a. Identify a table in Sakila that violates 3NF. Describe the transitive dependencies present and outline the steps to normalize the table to 3NF.

-- The staff table is now in 3NF as there are no transitive dependencies
-- Here's the structure of the staff table after normalization:
DESCRIBE staff;

#QUES-4 Normalization Process:
#a. Take a specific table in Sakila and guide through the process of normalizing it from the initial unnormalized form up to at least 2NF.
#We started with an unnormalized table (rental) with redundant information.We applied 1NF to ensure atomic values and a primary key.
#We applied 2NF by removing partial dependencies and splitting the table into customer, film, and rental tables.

#QUES-5  CTE Basics:
#a. Write a query using a CTE to retrieve the distinct list of actor names and the number of films they have acted in from the actor and film_actor tables.
WITH ActorFilmCount AS (
    SELECT 
        a.first_name || ' ' || a.last_name AS actor_name,  -- Concatenate first and last name for full name
        COUNT(fa.film_id) AS num_of_films
    FROM actor a
    JOIN film_actor fa ON a.actor_id = fa.actor_id  -- Join the actor and film_actor tables
    GROUP BY a.actor_id
)
SELECT DISTINCT actor_name, num_of_films
FROM ActorFilmCount
ORDER BY actor_name;

#QUES-6. CTE with Joins
#a. Create a CTE that combines information from the film and language tables to display the film title, language name, and rental rate.

WITH FilmLanguageInfo AS (
    SELECT 
        f.title AS film_title,                     -- Film title from the film table
        l.name AS language_name,                   -- Language name from the language table
        f.rental_rate                             -- Rental rate from the film table
    FROM film f
    JOIN language l ON f.language_id = l.language_id  -- Join film and language tables
)
SELECT film_title, language_name, rental_rate
FROM FilmLanguageInfo
ORDER BY film_title;

#QUES-7. CTE for Aggregation:
# a. Write a query using a CTE to find the total revenue generated by each customer (sum of payments) from the customer and payment tables.

WITH CustomerRevenue AS (
    SELECT 
        c.customer_id,                  -- Customer ID from the customer table
        c.first_name || ' ' || c.last_name AS customer_name,  -- Concatenate first and last names to form full name
        SUM(p.amount) AS total_revenue  -- Sum of payments for each customer
    FROM customer c
    JOIN payment p ON c.customer_id = p.customer_id  -- Join customer and payment tables on customer_id
    GROUP BY c.customer_id, c.first_name, c.last_name  -- Group by customer_id to get total revenue per customer
)
SELECT customer_name, total_revenue
FROM CustomerRevenue
ORDER BY total_revenue DESC;

#QUES-8. CTE with Window Functions:
# a. Utilize a CTE with a window function to rank films based on their rental duration from the film table.

WITH FilmRanking AS (
    SELECT 
        f.title AS film_title,            -- Film title from the film table
        f.rental_duration,                -- Rental duration from the film table
        RANK() OVER (ORDER BY f.rental_duration DESC) AS rental_rank  -- Rank films based on rental duration
    FROM film f
)
SELECT film_title, rental_duration, rental_rank
FROM FilmRanking
ORDER BY rental_rank;

#QUES-9 CTE and Filtering:
# a. Create a CTE to list customers who have made more than two rentals, and then join this CTE with the customer table to retrieve additional customer details.

WITH CustomerRentalCount AS (
    SELECT 
        p.customer_id,               -- Customer ID from the payment table
        COUNT(p.rental_id) AS rental_count  -- Count the number of rentals made by each customer
    FROM payment p
    GROUP BY p.customer_id
    HAVING COUNT(p.rental_id) > 2   -- Only include customers who have made more than two rentals
)
SELECT 
    c.customer_id,                -- Customer ID from the customer table
    c.first_name,                 -- Customer's first name
    c.last_name,                  -- Customer's last name
    c.email,                      -- Customer's email
    c.address_id,                 -- Customer's address ID
    crc.rental_count              -- Number of rentals made by the customer from the CTE
FROM CustomerRentalCount crc
JOIN customer c ON crc.customer_id = c.customer_id  -- Join CTE with customer table on customer_id
ORDER BY c.first_name, c.last_name;

#QUES-10 CTE for Date Calculations:
#a. Write a query using a CTE to find the total number of rentals made each month, considering the rental_date from the rental table

WITH MonthlyRentalCount AS (
    SELECT 
        YEAR(r.rental_date) AS rental_year,         -- Extract the year from rental_date
        MONTH(r.rental_date) AS rental_month,       -- Extract the month from rental_date
        COUNT(r.rental_id) AS total_rentals         -- Count the number of rentals for each month
    FROM rental r
    GROUP BY YEAR(r.rental_date), MONTH(r.rental_date)   -- Group by year and month
)
SELECT 
    rental_year, 
    rental_month, 
    total_rentals
FROM MonthlyRentalCount
ORDER BY rental_year DESC, rental_month DESC;

#Ques-11 CTE and Self-Join:
# a. Create a CTE to generate a report showing pairs of actors who have appeared in the same film together, using the film_actor table.

WITH ActorPairs AS (
    SELECT 
        fa1.actor_id AS actor1_id,     -- First actor in the pair
        fa2.actor_id AS actor2_id,     -- Second actor in the pair
        fa1.film_id                    -- Film in which both actors appeared
    FROM film_actor fa1
    JOIN film_actor fa2 
        ON fa1.film_id = fa2.film_id  -- Join on film_id to find actors in the same film
    WHERE fa1.actor_id < fa2.actor_id  -- Ensure each pair is unique by avoiding reverse pairs
)
SELECT 
    a1.first_name || ' ' || a1.last_name AS actor1_name,  -- First actor's name
    a2.first_name || ' ' || a2.last_name AS actor2_name,  -- Second actor's name
    ap.film_id                                          -- Film ID where both actors appeared
FROM ActorPairs ap
JOIN actor a1 ON ap.actor1_id = a1.actor_id  -- Join to get first actor's details
JOIN actor a2 ON ap.actor2_id = a2.actor_id  -- Join to get second actor's details
ORDER BY ap.film_id, actor1_name, actor2_name;

#QUES-12 CTE for Recursive Search:
# a. Implement a recursive CTE to find all employees in the staff table who report to a specific manager, considering the reports_to column

WITH RECURSIVE EmployeeHierarchy AS (
    -- Base case: Start with the manager (e.g., manager with staff_id = 1)
    SELECT 
        s.staff_id, 
        s.first_name || ' ' || s.last_name AS employee_name, 
        s.reports_to
    FROM staff s
    WHERE s.staff_id = 1  -- Specify the manager's staff_id (e.g., staff_id = 1 for the manager)

    UNION ALL

    -- Recursive case: Find all employees who report to those in the previous step
    SELECT 
        s.staff_id, 
        s.first_name || ' ' || s.last_name AS employee_name, 
        s.reports_to
    FROM staff s
    JOIN EmployeeHierarchy eh ON s.reports_to = eh.staff_id
)
SELECT staff_id, employee_name
FROM EmployeeHierarchy
ORDER BY employee_name;
