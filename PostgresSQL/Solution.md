# Exercises Solution (MySQL)

## Setup

- Follow this [guide](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database) to install PostgresSQL on WSL2.

- Install  [MySQL](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2) Extension on `VSCode`.

- Run the command `$ sudo service postgresql start`.

- Run the command `$ sudo -u postgres psql`.

- Create a new connection with the extension, using the credentials you created while installing PostgreSQL earlier. Make sure you choose server type as `PostgresSQL`.

- In Postgres Shell, create a new Database `# create database "LearnSQL";`.

- Quit the shell`# \q`.

- Enter the following command `$ psql -h 127.0.0.1 -U postgres "LearnSQL" < sqlexbackup.sql` or `psql -h 127.0.0.1 -U postgres "LearnSQL" < northwindexbackup.sql`, you might need to replace the backup with it's full path extension.

- Enter the following: 
  - `$ psql -h 127.0.0.1 -U postgres "LearnSQL"`.
  - `# CREATE ROLE root WITH LOGIN ENCRYPTED PASSWORD 'password';`.
  - `# GRANT CONNECT ON DATABASE "LearnSQL" TO root;`.
  - `# GRANT USAGE ON SCHEMA public TO root;`.
  - `# GRANT SELECT ON ALL TABLES IN SCHEMA public TO root;`.
  - `# \q`.

- Enter `$ psql -h 127.0.0.1 -U root "LearnSQL"` to start executing SQL commands in terminal or use a `VSCode` extension.

## Solutions

### Retrieve data from tables

#### 1. Write a SQL statement to display all the information of all salesmen.

```sql
SELECt * FROM salesman;
```

<br>

#### 2. Write a SQL statement to display a string "This is SQL Exercise, Practice and Solution".

```sql
SELECT 'This is SQL Exercise, Practice and Solution';
```

<br>

#### 3. Write a query to display three numbers in three columns.

```sql
SELECT 1, 2, 3;
```

<br>

#### 4. Write a query to display the sum of two numbers 10 and 15 from RDMS sever.

```sql
SELECT 10 + 15;
```

<br>

#### 5. Write a query to display the result of an arithmetic expression.

```sql
SELECT 1 + 1 - 1 * 1;
```

<br>

#### 6. Write a SQL statement to display specific columns like name and commission for all the salesmen.

```sql
SELECT name, commission FROM salesman;
```

<br>

#### 7. Write a query to display the columns in a specific order like order date, salesman id, order number and purchase amount from for all the orders.

```sql
SELECT ord_date, salesman_id, ord_no, purch_amt FROM orders;
```

<br>

#### 8. From the following table, write a SQL query to find the unique salespeople ID. Return salesman_id.

```sql
SELECT DISTINCT salesman_id FROM orders;
```

<br>

#### 9. From the following table, write a SQL query to find the salespeople who lives in the City of 'Paris'. Return salesperson's name, city.

```sql
SELECT name, city FROM salesman
WHERE city = 'Paris';
```

<br>

#### 10. From the following table, write a SQL query to find those customers whose grade is 200. Return customer_id, cust_name, city, grade, salesman_id.

```sql
SELECT * FROM customer
WHERE grade = 200;
```

<br>

#### 11. From the following table, write a SQL query to find the orders, which are delivered by a salesperson of ID. 5001. Return ord_no, ord_date, purch_amt.

```sql
SELECT ord_no, ord_date, purch_amt FROM orders
WHERE salesman_id = 5001;
```

#### 12. From the following table, write a SQL query to find the Nobel Prize winner(s) in the year 1970. Return year, subject and winner.

```sql
SELECT year, subject, winner FROM nobel_win
WHERE year = 1970;
```

<br>

#### 13. From the following table, write a SQL query to find the Nobel Prize winner in 'Literature' in the year 1971. Return winner.

```sql
SELECT winner FROM nobel_win
WHERE subject = 'Literature' AND year = 1971;
```

<br>

#### 14. From the following table, write a SQL query to find the Nobel Prize winner 'Dennis Gabor'. Return year, subject.

```sql
SELECT year, subject FROM nobel_win
WHERE winner = 'Dennis Gabor';
```

<br>

#### 15. From the following table, write a SQL query to find the Nobel Prize winners in 'Physics' since the year 1950. Return winner.

```sql
SELECT winner FROM nobel_win
WHERE subject = 'Physics' AND year > 1950;
```

<br>

#### 16. From the following table, write a SQL query to find the Nobel Prize winners in 'Chemistry' between the years 1965 to 1975. Begin and end values are included. Return year, subject, winner, and country.

```sql
SELECT year, subject, winner, country FROM nobel_win
WHERE subject = 'Chemistry' AND year BETWEEN 1965 AND 1975;
```

#### 17. Write a SQL query to show all details of the Prime Ministerial winners after 1972 of Menachem Begin and Yitzhak Rabin.

```sql
SELECT * FROM nobel_win
WHERE category = 'Prime Minister'
AND year > 1972
AND winner IN ('Menachem Begin', 'Yitzhak Rabin');
```

<br>

#### 18. From the following table, write a SQL query to find the details of the winners whose first name matches with the string 'Louis'. Return year, subject, winner, country, and category.

```sql
SELECT * FROM nobel_win
WHERE winner LIKE 'Louis %';
```

<br>

#### 19. From the following table, write a SQL query to combine the winners in Physics, 1970 and in Economics, 1971. Return year, subject, winner, country, and category.

```sql
SELECT * FROM nobel_win
WHERE (subject = 'Physics' AND year = 1970) 
OR (subject = 'Economics' AND year = 1971);
```

<br>

#### 20. From the following table, write a SQL query to find the Nobel Prize winners in 1970 excluding the subjects Physiology and Economics. Return year, subject, winner, country, and category.

```sql
SELECT * FROM nobel_win
WHERE year = 1970 
AND subject NOT IN ('Physiology', 'Economics');
```

<br>

#### 21. From the following table, write a SQL query to combine the winners in 'Physiology' before 1971 and winners in 'Peace' on or after 1974. Return year, subject, winner, country, and category.

```sql
SELECT * FROM nobel_win
WHERE (subject = 'Physiology' AND year < 1971)
OR (subject = 'Peace' AND year >= 1974);
```

<br>

#### 22. From the following table, write a SQL query to find the details of the Nobel Prize winner 'Johannes Georg Bednorz'. Return year, subject, winner, country, and category.

```sql
SELECT * FROM nobel_win
WHERE winner = 'Johannes Georg Bednorz';
```

<br>

#### 23. From the following table, write a SQL query to find the Nobel Prize winners for the subject not started with the letter 'P'. Return year, subject, winner, country, and category. Order the result by year, descending.

```sql
SELECT * FROM nobel_win
WHERE subject NOT LIKE 'P%'
ORDER BY year DESC;
```

<br>

#### ** 24. From the following table, write a SQL query to find the details of 1970 Nobel Prize winners. Order the result by subject, ascending except ‘Chemistry’ and ‘Economics’ which will come at the end of result set. Return year, subject, winner, country, and category.

```sql
SELECT * FROM

(SELECT *, 1 AS priority FROM nobel_win
WHERE subject NOT IN ('Economics', 'Chemistry') AND year = 1970

UNION

SELECT *, 2 AS priority FROM nobel_win
WHERE subject IN ('Economics', 'Chemistry') and year = 1970
ORDER BY priority, subject, winner)

TEMP;
```

<br>

#### 25. From the following table, write a SQL query to select a range of products whose price is in the range Rs.200 to Rs.600. Begin and end values are included. Return pro_id, pro_name, pro_price, and pro_com.

```sql
SELECT * FROM item_mast
WHERE pro_price BETWEEN 200 AND 600;
```

<br>

#### 26. From the following table, write a SQL query to calculate the average price for manufacturer code equal to 16. Return avg.

```sql
SELECT AVG(pro_price) FROM item_mast
WHERE pro_com = 16;
```

<br>

#### 27. From the following table, write a SQL query to display the pro_name as 'Item Name' and pro_priceas 'Price in Rs.' 

```sql
SELECT pro_name AS "Item Name", pro_price AS "Price in Rs"
FROM item_mast;
```

<br>

### 28. From the following table, write a SQL query to find the items whose prices are higher than or equal to $250. Order the result by product price in descending, then product name in ascending. Return pro_name and pro_price.

```sql
SELECT pro_name , pro_price FROM item_mast
WHERE pro_price >= 250
ORDER BY pro_price DESC, pro_name ASC;
```

<br>

#### 29. From the following table, write a SQL query to calculate average price of the items of each company. Return average price and company code.

```sql
SELECT AVG(pro_price), pro_com FROM item_mast
GROUP BY pro_com;
```

<br>

#### 30. From the following table, write a SQL query to find the cheapest item(s). Return pro_name and, pro_price.

```sql
SELECT pro_name, pro_price FROM item_mast
WHERE pro_price = (
    SELECT MIN(pro_price) FROM item_mast
);
```

<br>

#### 31. From the following table, write a SQL query to find unique last name of all employees. Return emp_lname.

```sql
SELECt DISTINCT emp_lname FROM emp_details;
```

<br>

#### 32. From the following table, write a SQL query to find the details of employees whose last name is 'Snares'. Return emp_idno, emp_fname, emp_lname, and emp_dept.

```sql
SELECT * FROM emp_details
WHERE emp_lname = 'Snares';
```

<br>

#### 33. From the following table, write a SQL query to find the details of the employees who work in the department 57. Return emp_idno, emp_fname, emp_lname and emp_dept.

```sql
SELECT * FROM emp_details
WHERE emp_dept = 57;
```

### Boolean and Relational Operators

#### 1. From the following table, write a SQL query to find the details of the customers who have a gradevalue above 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT * FROM customer
WHERE grade > 100; 
```

<br>

#### 2. From the following table, write a SQL query to find all the customers in ‘New York’ city who have a grade value above 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT * FROM customer
WHERE grade > 100
AND city = 'New York'; 
```

<br>

#### 3. From the following table, write a SQL query to find the customers who belong to either the city ‘New York’ or have a grade above 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT * FROM customer
WHERE grade > 100
OR city = 'New York'; 
```

<br>

#### 4. From the following table, write a SQL query to find the customers who belong to either the city ‘New York’ or not have a grade above 100. Return customer_id, cust_name, city, grade, and salesman_id. 

```sql
SELECT * FROM customer
WHERE NOT grade > 100
OR city = 'New York'; 
```

<br>

#### 5. From the following table, write a SQL query to find those customers who belong to neither the ‘New York’ city nor their grade value exceeds 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT * FROM customer
WHERE NOT grade > 100
AND NOT city = 'New York'; 
```

<br>

#### 6. From the following table, write a SQL query to find details of all order excluding combination of ord_date equal to '2012-09-10' and salesman_id higher than 5005 or purch_amt greater than 1000. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT * FROM orders
WHERE NOT ((ord_date = '2012-09-10'
AND salesman_id > 5005)
OR purch_amt > 1000); 
```

<br>

#### 7. From the following table, write a SQL query to find the details of those salespeople whose commissions range from 0.10 to0.12. Return salesman_id, name, city, and commission.

```sql
SELECT * FROM salesman
WHERE commission > 0.10 
AND commission <0.12; 
```

<br>

#### 8. From the following table, write a SQL query to find details of all order where purchase amount less than 200 or excluding combination of order date greater than or equal to '2012-02-10' and customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT * FROM orders
WHERE purch_amt < 200 
OR NOT (
    ord_date >= '2012-02-10'
    AND customer_id < 3009
); 
```

<br>

#### 9. From the following table, write a SQL query to find all orders subject to following conditions. Exclude combination of order date equal to '2012-08-17' or customer ID higher than 3005 and purchase amount less than 1000.

```sql
SELECT * FROM orders
WHERE NOT (
    ord_date = '2012-08-17'
    OR(customer_id > 3005
    AND purch_amt < 1000)
); 
```

<br>

#### ** 10. Write a SQL query to display order number, purchase amount, the achieved and unachieved percentage (%) for those order which exceeds the 50% of the target value of 6000.

```sql
SELECT ord_no, purch_amt,
(100 * purch_amt) / 6000 AS "achieved",
(100 * ( 6000 - purch_amt) / 6000) AS "unachieved"
FROM orders
WHERE 100 * purch_amt / 6000 > 50; 
```

<br>

#### 11. From the following table, write a SQL query to find the details of all employees whose last name is ‘Dosni’ or ‘Mardy’. Return emp_idno, emp_fname, emp_lname, and emp_dept.

```sql
SELECT * FROM emp_details
WHERE emp_lname = 'Dosni' 
OR emp_lname = 'Mardy';
```

<br>

#### 12. From the following table, write a SQL query to find the employees who works at depart 47 or 63. Return emp_idno, emp_fname, emp_lname, and emp_dept.

```sql
SELECT * FROM emp_details
WHERE emp_dept = 47 
OR emp_dept = 63;
```

### Retrieve data from tables

#### 1. From the following table, write a SQL query to find the details of those salespeople who come from the 'Paris' City or 'Rome' City. Return salesman_id, name, city, commission.

```sql
SELECT * FROM salesman
WHERE city ='Paris'
OR city = 'Rome';
```

<br>

#### 2. From the following table, write a SQL query to find the details of those salespeople who come from any of the City 'Paris' or 'Rome'. Return salesman_id, name, city, commission.

```sql
SELECT * FROM salesman
WHERE city IN ('Paris', 'Rome');
```

<br>

#### 3. From the following table, write a SQL query to find the details of those salespeople who live in cities apart from 'Paris' and 'Rome'. Return salesman_id, name, city, commission.

```sql
SELECT * FROM salesman
WHERE city NOT IN ('Paris', 'Rome');
```

<br>

#### 4. From the following table, write a SQL query to find the details of the customers whose ID belongs to any of the values 3007, 3008 and 3009. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT * FROM customer
WHERE customer_id IN (3007, 3008, 3009);
```

<br>

#### 5. From the following table, write a SQL query to find the details of salespeople who get the commission in the range from 0.12 to 0.14 (begin and end values are included). Return salesman_id, name, city, and commission.

```sql
SELECT * FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

<br>

#### 6. From the following table, write a SQL query to select orders value within a range 500, 4000 (begin and end values are included). Exclude orders amount 948.50 and 1983.43. Return ord_no, purch_amt, ord_date, customer_id, and salesman_id.

```sql
SELECT * FROM orders
WHERE (purch_amt BETWEEN 500 AND 4000)
AND (purch_amt NOT IN (948.50, 1983.43));
```

<br>

#### 7. From the following table, write a SQL query to find the details of those salespeople whose name starts with any letter within 'A' and 'L' (not inclusive). Return salesman_id, name, city, commission.

```sql
SELECT * FROM salesman
WHERE name BETWEEN 'B' AND 'K';
```

<br>

#### 8. From the following table, write a SQL query to find the details of all salespeople except whose name starts with any letter within 'A' and 'L' (not inclusive). Return salesman_id, name, city, commission. 

```sql
SELECT * FROM salesman
WHERE name NOT BETWEEN 'B' AND 'K';
```

<br>

#### 9. From the following table, write a SQL query to find the details of the customers whose name begins with the letter 'B'. Return customer_id, cust_name, city, grade, salesman_id. 

```sql
SELECT * FROM customer
WHERE cust_name LIKE 'B%';
```

<br>

#### 10. From the following table, write a SQL query to find the details of the customers whose names end with the letter 'n'. Return customer_id, cust_name, city, grade, salesman_id.

```sql
SELECT * FROM customer
WHERE cust_name LIKE '%n';
```

<br>

#### 11. From the following table, write a SQL query to find the details of those salespeople whose name starts with ‘N’ and the fourth character is 'l'. Rests may be any character. Return salesman_id, name, city, commission.

```sql
SELECT * FROM salesman
WHERE name LIKE 'N__l%';
```

<br>

#### 12. From the following table, write a SQL query to find those rows where col1 contains the escape character underscore ( _ ). Return col1.

```sql
SELECT * FROM testtable
WHERE col1 LIKE '%\_%';
```

<br>

#### 13. From the following table, write a SQL query to find those rows where col1 does not contain the escape character underscore ( _ ). Return col1.

```sql
SELECT * FROM testtable
WHERE col1 NOT LIKE '%\_%';
```

<br>

#### 14. From the following table, write a SQL query to find those rows where col1 contains the forward slash character ( / ). Return col1.

```sql
SELECT * FROM testtable
WHERE col1  LIKE '%/%';
```

<br>

#### 15. From the following table, write a SQL query to find those rows where col1 does not contain the forward slash character ( / ). Return col1

```sql
SELECT * FROM testtable
WHERE col1  NOT LIKE '%/%';
```

<br>

#### 16. From the following table, write a SQL query to find those rows where col1 contains the string ( _/ ). Return col1.

```sql
SELECT * FROM testtable
WHERE col1 LIKE '%\_/%';
```

<br>

#### 17. From the following table, write a SQL query to find those rows where col1 does not contain the string ( _/ ). Return col1.

```sql
SELECT * FROM testtable
WHERE col1 NOT LIKE '%\_/%';
```

<br>

#### 18. From the following table, write a SQL query to find those rows where col1 contains the character percent ( % ). Return col1.

```sql
SELECT * FROM testtable
WHERE col1 LIKE '%\%%';
```

<br>

#### 19. From the following table, write a SQL query to find those rows where col1 does not contain the character percent ( % ). Return col1.

```sql
SELECT * FROM testtable
WHERE col1 NOT LIKE '%\%%';
```

<br>

#### 20. From the following table, write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id.

```sql
SELECT * FROM customer
WHERE grade IS NULL;
```

<br>

#### 21. From the following table, write a SQL query to find all those customers whose grade value exists. Return customer_id, cust_name, city, grade, salesman_id. 

```sql
SELECT * FROM customer
WHERE grade IS NOT NULL;
```

<br>

#### 22. From the following table, write a SQL query to find the employees whose last name begins with the character 'D'. Return emp_idno, emp_fname, emp_lname and emp_dept.

```sql
SELECT * FROM emp_details
WHERE emp_lname LIKE 'D%';
```

<br>

### Aggregate Functions

#### 1. From the following table, write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

```sql
SELECT SUM(purch_amt) FROM orders;
```

<br>

#### 2. From the following table, write a SQL query to calculate average purchase amount of all orders. Return average purchase amount.

```sql
SELECT AVG(purch_amt) FROM orders;
```

<br>

#### 3. From the following table, write a SQL query to count the number of unique salespeople. Return number of salespeople.

```sql
SELECT  COUNT(DISTINCT salesman_id) FROM orders;
```

<br>

#### 4. From the following table, write a SQL query to count the number of customers. Return number of customers.

```sql
SELECT  COUNT(DISTINCT customer_id) FROM customer;
```

<br>

#### 5. From the following table, write a SQL query to find the number of customers who got at least a gradation for his/her activity.

```sql
SELECT  COUNT(DISTINCT customer_id) FROM customer
WHERE grade IS NOT NULL;
```

<br>

#### 6. From the following table, write a SQL query to find the maximum purchase amount.

```sql
SELECT  MAX(purch_amt) FROM orders;
```

<br>

#### 7. From the following table, write a SQL query to find the minimum purchase amount.

```sql
SELECT  MIN(purch_amt) FROM orders;
```

<br>

#### 8. From the following table, write a SQL query to find the highest grade of the customers for each of the city. Return city, maximum grade.  

```sql
SELECT  city, MAX(grade) FROM customer
GROUP BY city;
```

<br>

#### 9. From the following table, write a SQL query to find the highest purchase amount ordered by each customer. Return customer ID, maximum purchase amount. 

```sql
SELECT  customer_id, MAX(purch_amt)  FROM orders
GROUP BY customer_id;
```

<br>

#### 10. From the following table, write a SQL query to find the highest purchase amount ordered by each customer on a particular date. Return, order date and highest purchase amount

```sql
SELECT  customer_id, ord_date , MAX(purch_amt) FROM orders
GROUP BY customer_id, ord_date;
```

<br>

#### 11. From the following table, write a SQL query to find the highest purchase amount on '2012-08-17' by each salesperson. Return salesperson ID, purchase amount.

```sql
SELECT salesman_id, MAX(purch_amt) FROM orders
WHERE ord_date = '2012-08-17'
GROUP BY salesman_id;
```

<br>

#### 12. From the following table, write a SQL query to find highest order (purchase) amount by each customer in a particular order date. Filter the result by highest order (purchase) amount above 2000.00. Return customer id, order date and maximum purchase amount.

```sql
SELECT customer_id, ord_date, MAX(purch_amt) FROM orders
WHERE purch_amt > 2000
GROUP BY customer_id, ord_date;
```

<br>

#### 13. From the following table, write a SQL query to find the maximum order (purchase) amount in the range 2000, 6000 (Begin and end values are included.) by combination of each customer and order date. Return customer id, order date and maximum purchase amount.

```sql
SELECT customer_id, ord_date, MAX(purch_amt) FROM orders
WHERE purch_amt BETWEEN 2000 AND 6000
GROUP BY customer_id, ord_date;
```

<br>

#### 14. From the following table, write a SQL query to find the maximum order (purchase) amount by the combination of each customer and order date. Filter the rows for maximum order (purchase) amount is either 2000, 3000, 5760, 6000. Return customer id, order date and maximum purchase amount.

```sql
SELECT customer_id, ord_date, MAX(purch_amt) FROM orders
WHERE purch_amt IN (2000, 3000, 5760, 6000)
GROUP BY customer_id, ord_date;
```

<br>

#### 15. From the following table, write a SQL query to find the maximum order (purchase) amount by each customer. The customer ID should be in the range 3002 and 3007(Begin and end values are included.). Return customer id and maximum purchase amount.

```sql
SELECT customer_id, MAX(purch_amt) FROM orders
WHERE customer_id BETWEEN 3002 AND 3007
GROUP BY customer_id;
```

<br>

#### 16. From the following table, write a SQL query to find the maximum order (purchase) amount for each customer. The customer ID should be in the range 3002 and 3007(Begin and end values are included.). Filter the rows for maximum order (purchase) amount is higher than 1000. Return customer id and maximum purchase amount.

```sql
SELECT customer_id, MAX(purch_amt) FROM orders
WHERE customer_id BETWEEN 3002 AND 3007
GROUP BY customer_id
HAVING MAX(purch_amt) > 1000;
```

<br>

#### 17. From the following table, write a SQL query to find the maximum order (purchase) amount generated by each salesperson. Filter the rows for the salesperson ID is in the range 5003 and 5008 (Begin and end values are included.). Return salesperson id and maximum purchase amount.

```sql
SELECT salesman_id, MAX(purch_amt) FROM orders
WHERE salesman_id BETWEEN 5003 AND 5008
GROUP BY salesman_id;
```

<br>

#### 18. From the following table, write a SQL query to count all the orders generated on '2012-08-17'. Return number of orders.

```sql
SELECT COUNT(ord_no) FROM orders
WHERE ord_date = '2012-08-17';
```

<br>

#### 19. From the following table, write a SQL query to count number of salespeople who belongs to a city. Return number of salespeople.

```sql
SELECT COUNT(salesman_id) FROM salesman
WHERE city IS NOT NULL;
```

<br>

#### 20. From the following table, write a SQL query to count number of orders by the combination of each order date and salesperson. Return order date, salesperson id.

```sql
SELECT ord_date, salesman_id, COUNT(ord_no) FROM orders
GROUP BY ord_date, salesman_id;
```

<br>

#### 21. From the following table, write a SQL query to calculate the average product price. Return average product price.

```sql
SELECT AVG(pro_price) FROM item_mast;
```

<br>

#### 22. From the following table, write a SQL query to count number of products where product price is higher than or equal to 350. Return number of products.

```sql
SELECT COUNT(pro_id) FROM item_mast
WHERE pro_price >= 350;
```

<br>

#### 23. From the following table, write a SQL query to compute the average price for unique companies. Return average price and company id.

```sql
SELECT AVG(pro_price), pro_com FROM item_mast
GROUP BY pro_com;
```

<br>

#### 24. From the following table, write a SQL query to compute the sum of the allotment amount of all departments. Return sum of the allotment amount.

```sql
SELECT SUM(dpt_allotment) FROM emp_department;
```

<br>

#### 25. From the following table, write a SQL query to find the number of employees in each department. Return department code and number of employees.

```sql
SELECT emp_dept, COUNT(emp_idno) FROM emp_details
GROUP BY emp_dept;
```

<br>

### Formatting query output

#### 1. From the following table, write a SQL query to select all the salespeople. Return salesman_id, name, city, commission with the percent sign (%).

```sql
SELECT salesman_id, name, city, 
CONCAT((commission * 100), '%') FROM salesman;
```

<br>

#### 2. From the following table, write a SQL query to find the number of orders booked for each day. Return the result in a format like "For 2001-10-10 there are 15 orders".".

```sql
SELECT CONCAT('For ', ord_date, ' there are ', COUNT(ord_no), ' orders.')
```

<br>

#### 3. From the following table, write a SQL query to find all the orders. Sort the result-set in ascending order by ord_no. Return all fields.

```sql
SELECT * FROM orders
ORDER BY ord_no ASC;
```

<br>

#### 4. From the following table, write a SQL query to find all the orders. Sort the result-set in descending order by ord_date. Return all fields. 

```sql
SELECT * FROM orders
ORDER BY ord_no DESC;
```

<br>

#### 5. From the following table, write a SQL query to find all the orders. Sort the result-set in descending order by ord_date and purch_amt. Return all fields.

```sql
SELECT * FROM orders
ORDER BY ord_date, purch_amt DESC;
```

<br>

#### 6. From the following table, write a SQL query to find all the customers. Sort the result-set by customer_id. Return cust_name, city, grade. 

```sql
SELECT cust_name, city, grade FROM customer
ORDER BY customer_id ASC;
```

<br>

#### 7. From the following table, write a SQL query to calculate the maximum purchase amount generated by each sales person for every order date. Sort the result-set by sales person id and order date in ascending order. Return sales person id, order date and maximum purchase amount.

```sql
SELECT salesman_id, ord_date, MAX(purch_amt) FROM orders
GROUP BY salesman_id, ord_date
ORDER BY salesman_id, ord_date ASC;
```

<br>

#### 8. From the following table, write a SQL query to find all the customers. Sort the result-set in descending order on 3rd field. Return customer name, city and grade.

```sql
SELECT cust_name, city, grade FROM customer
ORDER BY 3 DESC;
```

<br>

#### 9. From the following table, write a SQL query to count the unique orders, highest purchase amount for each customer. Sort the result-set in descending order on 2nd field. Return customer ID, number of distinct orders and highest purchase amount by each customer. 

```sql
SELECT customer_id, COUNT(DISTINCT ord_no), MAX(purch_amt) FROM orders
GROUP BY customer_id
ORDER BY 2 DESC;
```

<br>

#### 10. From the following table, write a SQL query to calculate summation of purchase amount, total commission (15% for all salesmen) by each order date. Sort the result-set on order date. Return order date, summation of purchase amount and commission. 

```sql
SELECT ord_date, SUM(purch_amt),SUM(purch_amt * 0.15)  FROM orders
GROUP BY ord_date
ORDER BY ord_date ASC;
```

<br>

### Query on Multiple Tables

#### 1. From the following tables, write a SQL query to find the salespersons and customers who live in same city. Return customer name, salesperson name and salesperson city.

```sql
SELECT customer.cust_name, salesman.name, salesman.city FROM salesman
JOIN customer ON salesman.salesman_id = customer.salesman_id;
```

<br>

#### 2. From the following tables, write a SQL query to find all the customers along with the salesperson who works for them. Return customer name, and salesperson name.

```sql
SELECT customer.cust_name, salesman.name FROM salesman
JOIN customer ON salesman.salesman_id = customer.salesman_id;
```

<br>

#### 3. From the following tables, write a SQL query to find those sales people who generated orders for their customers but not located in the same city. Return ord_no, cust_name, customer_id (orders table), salesman_id (orders table).

```sql
SELECT orders.ord_no, customer.cust_name, customer.customer_id, salesman.salesman_id FROM salesman
JOIN customer ON salesman.salesman_id = customer.salesman_id
JOIN orders ON orders.customer_id = customer.customer_id
WHERE salesman.city != customer.city;
```

<br>

#### 4. From the following tables, write a SQL query to find those orders made by customers. Return order number, customer name.

```sql
SELECT orders.ord_no, customer.cust_name FROM orders
JOIN customer ON orders.customer_id = customer.customer_id;
```

<br>

#### 5. From the following tables, write a SQL query to find those customers where each customer has a grade and served by at least a salesperson who belongs to a city. Return cust_name as "Customer", grade as "Grade" and order_no as "Order No.".

```sql
SELECT customer.cust_name AS "Customer", customer.grade AS "Grade", orders.ord_no AS "Order No." FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id
JOIN orders ON  customer.customer_id = orders.customer_id
WHERE customer.grade IS NOT NULL
AND salesman.city IS NOT NULL;
```

<br>

#### 6. From the following table, write a SQL query to find those customers who served by a salesperson and the salesperson works at the commission in the range 12% to 14% (Begin and end values are included.). Return cust_name AS "Customer", city AS "City".

```sql
SELECT customer.cust_name AS "Customer", customer.city AS "City" FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id
WHERE salesman.commission BETWEEN 0.12 AND 0.14;
```

<br>

#### 7. From the following tables, write a SQL query to find those orders executed by the salesperson, ordered by the customer whose grade is greater than or equal to 200. Compute purch_amt*commission as "Commission". Return customer name, commission as "Commission%" and Commission.

```sql
SELECT orders.ord_no AS "Order No.", customer.cust_name AS "Customer", salesman.commission AS "Commission %", (orders.purch_amt * salesman.commission) AS "Commission" FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id
JOIN orders ON customer.customer_id = orders.customer_id
WHERE customer.grade >= 200;
```

<br>

#### 8. From the following table, write a SQL query to find those customers who made orders on October 5, 2012. Return customer_id, cust_name, city, grade, salesman_id, ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT customer.customer_id, customer.cust_name, customer.city, customer.grade, customer.salesman_id, orders.ord_no, orders.purch_amt, orders.ord_date, orders.customer_id FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id
JOIN orders ON customer.customer_id = orders.customer_id
WHERE orders.ord_date = '2012-10-05';
```

<br>

### SQL JOINS

#### 1. From the following tables write a SQL query to find the salesperson and customer who belongs to same city. Return Salesman, cust_name and city.

```sql
SELECT salesman.name, customer.cust_name, customer.city FROM salesman, customer
WHERE salesman.city = customer.city;
```

<br>

#### 2. From the following tables write a SQL query to find those orders where order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```sql
SELECT orders.ord_no, orders.purch_amt, customer.cust_name, customer.city FROM orders
JOIN customer ON orders.customer_id = customer.customer_id
WHERE orders.purch_amt BETWEEN 500 AND 2000;
```

<br>

#### 3. From the following tables write a SQL query to find the salesperson(s) and the customer(s) he handle. Return Customer Name, city, Salesman, commission.

```sql
SELECT customer.cust_name as "Customer Name", customer.city, salesman.name AS "Salesman", salesman.commission FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id;
```

<br>

#### 4. From the following tables write a SQL query to find those salespersons who received a commission from the company more than 12%. Return Customer Name, customer city, Salesman, commission.

```sql
SELECT customer.cust_name as "Customer Name", customer.city, salesman.name AS "Salesman", salesman.commission FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id
WHERE salesman.commission > 0.12;
```

<br>

#### 5. From the following tables write a SQL query to find those salespersons do not live in the same city where their customers live and received a commission from the company more than 12%. Return Customer Name, customer city, Salesman, salesman city, commission. 

```sql
SELECT customer.cust_name as "Customer Name", customer.city AS "Customer City", salesman.name AS "Salesman", salesman.city AS "Salesman City", salesman.commission AS "Commission" FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id
WHERE salesman.city != customer.city
AND salesman.commission > 0.12;
```

<br>

### 6. From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission.

```sql
SELECT orders.ord_no, orders.ord_date, orders.purch_amt, customer.cust_name as "Customer Name", customer.grade AS "Customer Grade", salesman.name AS "Salesman", salesman.commission AS "Commission" FROM orders
JOIN customer on orders.customer_id = customer.customer_id
JOIN salesman ON customer.salesman_id = salesman.salesman_id;
```

<br>

#### ** 7. Write a SQL statement to make a join on the tables salesman, customer and orders in such a form that the same column of each table will appear once and only the relational rows will come.

```sql
SELECT * FROM orders
NATURAL JOIN customer
NATURAL JOIN salesman;
```

<br>

#### 8. From the following tables write a SQL query to display the cust_name, customer city, grade, Salesman, salesman city. The result should be ordered by ascending on customer_id.

```sql
SELECT customer.cust_name, customer.city, customer.grade, salesman.name, salesman.city FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id
ORDER BY customer.customer_id ASC;
```

<br>

#### 9. From the following tables write a SQL query to find those customers whose grade less than 300. Return cust_name, customer city, grade, Salesman, saleman city. The result should be ordered by ascending customer_id.

```sql
SELECT customer.cust_name, customer.city, customer.grade, salesman.name, salesman.city FROM customer
JOIN salesman ON customer.salesman_id = salesman.salesman_id
WHERE customer.grade < 300
ORDER BY customer.customer_id ASC;
```

<br>

#### 10. Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to find that either any of the existing customers have placed no order or placed one or more orders.

```sql
SELECT customer.cust_name, customer.city, orders.ord_no, orders.ord_date, orders.purch_amt FROM customer
LEFT JOIN orders ON customer.customer_id = orders.customer_id
ORDER BY orders.ord_date ASC;
```

<br>

#### 11. Write a SQL statement to make a report with customer name, city, order number, order date, order amount salesman name and commission to find that either any of the existing customers have placed no order or placed one or more orders by their salesman or by own.

```sql
SELECT customer.cust_name, customer.city, orders.ord_no, orders.ord_date, orders.purch_amt, salesman.name, salesman.commission FROM customer
LEFT JOIN orders ON customer.customer_id = orders.customer_id
LEFT JOIN salesman ON customer.salesman_id = salesman.salesman_id;
```

<br>


#### 12. Write a SQL statement to make a list in ascending order for the salesmen who works either for one or more customer or not yet join under any of the customers.

```sql
SELECT salesman.salesman_id, salesman.name, customer.customer_id, customer.cust_name FROM salesman
LEFT JOIN customer ON salesman.salesman_id = customer.salesman_id;
```

<br>

#### ** 13. From the following tables write a SQL query to list all salespersons along with customer name, city, grade, order number, date, and amount. Condition for selecting list of salesmen : 1. Salesmen who works for one or more customer or, 2. Salesmen who not yet join under any customer, Condition for selecting list of customer : 3. placed one or more orders, or 4. no order placed to their salesman.

```sql
SELECT salesman.salesman_id, salesman.name, customer.customer_id, customer.cust_name, customer.city, customer.grade, orders.ord_no, orders.ord_date, orders.purch_amt FROM salesman
LEFT JOIN customer ON salesman.salesman_id = customer.salesman_id
LEFT JOIN orders ON salesman.salesman_id = orders.salesman_id;
```

<br>

#### 14. Write a SQL statement to make a list for the salesmen who either work for one or more customers or yet to join any of the customer. The customer may have placed, either one or more orders on or above order amount 2000 and must have a grade, or he may not have placed any order to the associated supplier. 

```sql
SELECT customer.customer_id, customer.cust_name, customer.city, customer.grade, salesman.salesman_id, salesman.name, orders.ord_no, orders.ord_date, orders.purch_amt FROM customer
RIGHT JOIN salesman ON salesman.salesman_id = customer.salesman_id
LEft JOIN orders ON customer.customer_id = orders.customer_id
WHERE orders.purch_amt >= 2000
OR customer.grade IS NOT NULL;
```

<br>

#### 15. Write a SQL statement to make a report with customer name, city, order no. order date, purchase amount for those customers from the existing list who placed one or more orders or which order(s) have been placed by the customer who is not on the list. 

```sql
SELECT customer.customer_id, customer.cust_name, customer.city, customer.grade, orders.ord_no, orders.ord_date, orders.purch_amt FROM customer
RIGHT JOIN orders ON customer.customer_id = orders.customer_id;
```

<br>

#### 16. Write a SQL statement to make a report with customer name, city, order no. order date, purchase amount for only those customers on the list who must have a grade and placed one or more orders or which order(s) have been placed by the customer who is neither in the list nor have a grade.

```sql
SELECT customer.customer_id, customer.cust_name, customer.city, customer.grade, orders.ord_no, orders.ord_date, orders.purch_amt FROM customer
RIGHT JOIN orders ON customer.customer_id = orders.customer_id
WHERE customer.grade IS NOT NULL;
```

<br>

#### 17. Write a SQL query to combine each row of salesman table with each row of customer table.

```sql
SELECT * FROM salesman
CROSS JOIN customer;
```

<br>


#### 18. Write a SQL statement to make a cartesian product between salesman and customer i.e. each salesman will appear for all customer and vice versa for that salesman who belongs to a city.

```sql
SELECT * FROM salesman
CROSS JOIN customer
WHERE salesman.city IS NOT NULL;
```

<br>

#### 19. Write a SQL statement to make a cartesian product between salesman and customer i.e. each salesman will appear for all customer and vice versa for those salesmen who belongs to a city and the customers who must have a grade.

```sql
SELECT * FROM salesman
CROSS JOIN customer
WHERE salesman.city IS NOT NULL
AND customer.grade IS NOT NULL;
```

<br>

#### 20. Write a SQL statement to make a cartesian product between salesman and customer i.e. each salesman will appear for all customer and vice versa for those salesmen who must belong a city which is not the same as his customer and the customers should have an own grade.

```sql
SELECT * FROM salesman
CROSS JOIN customer
WHERE salesman.city IS NOT NULL
AND customer.grade IS NOT NULL
AND salesman.city != customer.city;
```

<br>

#### 21. From the following tables write a SQL query to select all rows from both participating tables as long as there is a match between pro_com and com_id.

```sql
SELECT * FROM company_mast
JOIN item_mast ON company_mast.COM_ID = item_mast.PRO_COM;
```

<br>

#### 22. Write a SQL query to display the item name, price, and company name of all the products. 

```sql
SELECT item_mast.pro_name, item_mast.pro_price, item_mast.pro_com FROM item_mast
JOIN company_mast ON item_mast.PRO_COM = company_mast.COM_ID;
```

<br>

#### 23. From the following tables write a SQL query to calculate the average price of items of each company. Return average value and company name.

```sql
SELECT AVG(item_mast.pro_price), company_mast.com_name FROM item_mast
JOIN company_mast ON item_mast.PRO_COM = company_mast.COM_ID
GROUP BY company_mast.com_name;
```

<br>

#### 24. From the following tables write a SQL query to calculate and find the average price of items of each company higher than or equal to Rs. 350. Return average value and company name.

```sql
SELECT AVG(item_mast.pro_price), company_mast.com_name FROM item_mast
JOIN company_mast ON item_mast.PRO_COM = company_mast.COM_ID
GROUP BY company_mast.com_name
HAVING AVG(item_mast.pro_price) >= 350;
```

<br>

#### 25. From the following tables write a SQL query to find the most expensive product of each company. Return pro_name, pro_price and com_name.

```sql
SELECT item_mast.pro_name, item_mast.pro_price, company_mast.com_name FROM item_mast
JOIN company_mast ON item_mast.PRO_COM = company_mast.COM_ID
AND item_mast.pro_price = (
    SELECT MAX(item_mast.pro_price) FROM item_mast
    WHERE item_mast.PRO_COM = company_mast.COM_ID 
);
```

<br>

#### 26. From the following tables write a SQL query to display all the data of employees including their department.

```sql
SELECT * FROM emp_details
JOIN emp_department ON emp_details.emp_dept = emp_department.dpt_code;
```

<br>

#### 27. From the following tables write a SQL to display the first name and last name of each employee, along with the name and sanction amount for their department.

```sql
SELECT emp_details.emp_fname, emp_details.emp_lname, emp_department.dpt_name, emp_department.dpt_allotment FROM emp_details
JOIN emp_department ON emp_details.emp_dept = emp_department.dpt_code;
```

<br>

#### 28. From the following tables write a SQL query to find the departments with a budget more than Rs. 50000 and display the first name and last name of employees.

```sql
SELECT emp_details.emp_fname, emp_details.emp_lname, emp_department.dpt_name, emp_department.dpt_allotment FROM emp_details
JOIN emp_department ON emp_details.emp_dept = emp_department.dpt_code
WHERE emp_department.dpt_allotment > 50000;
```

<br>

#### 29. From the following tables write a SQL query to find the names of departments where more than two employees are working. Return dpt_name.

```sql
SELECT emp_department.dpt_name, COUNT(emp_details.emp_dept) FROM emp_department
JOIN emp_details ON emp_department.dpt_code = emp_details.emp_dept
GROUP BY emp_department.dpt_name
HAVING COUNT(emp_details.emp_dept) > 2;
```

<br>

### SUBQUERIES

#### 1. From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT orders.ord_no, orders.purch_amt, orders.customer_id, orders.salesman_id FROM orders
JOIN salesman ON orders.salesman_id = salesman.salesman_id
WHERE salesman.name = 'Paul Adam';
```

<br>


#### 2. From the following tables, write a SQL query to find all the orders, which are generated by those salespeople, who live in the city of London.Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

```sql
SELECT orders.ord_no, orders.purch_amt, orders.customer_id, orders.salesman_id FROM orders
JOIN salesman ON orders.salesman_id = salesman.salesman_id
WHERE salesman.city = 'London';
```

<br>
 
#### 3. From the following tables, write a SQL query to find the orders generated by the salespeople who works for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id. A customer can works only with a salespeople.

```sql
SELECT ord_no, purch_amt, customer_id, salesman_id FROM orders
WHERE salesman_id = (
    SELECT DISTINCT salesman_id FROM orders
    WHERE customer_id = 3007
);
```

<br>
 
#### 4. From the following tables, write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id. 

```sql
SELECT orders.ord_no, orders.purch_amt, orders.customer_id, orders.salesman_id FROM orders
WHERE orders.purch_amt > (
    SELECT AVG(purch_amt) FROM orders
    WHERE ord_date = ('2012-10-10')
);
```

<br>
 
#### 5. From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT ord_no, purch_amt, orders.customer_id, salesman_id FROM orders
WHERE salesman_id = (
    SELECT salesman_id FROM salesman
    WHERE city = 'New York'
);
```

<br>
 
#### 6. From the following tables, write a SQL query to find the commission of the salespeople work in Paris City. Return commission.

```sql
SELECT commission FROM salesman
WHERE salesman_id = (
    SELECT salesman_id FROM customer
    WHERE city = 'Paris'
);
```

<br>
 
#### ** 7. Write a query to display all the customers whose id is 2001 bellow the salesman ID of Mc Lyon.

```sql
SELECT cust_name FROM customer
WHERE customer_id = (
    SELECT salesman_id -2001 FROM salesman
    WHERE name = 'Mc Lyon'
);
```

<br>
 
#### ** 8. From the following tables, write a SQL query to count number of customers with grades above the average grades of New York City. Return grade and count.

```sql
SELECT grade, COUNT(*) FROM customer
GROUP BY grade
HAVING grade > (
    SELECT AVG(grade) FROM customer
    WHERE city = 'New York'
);
```

<br>
 
#### 9. From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

```sql
SELECT ord_no, purch_amt, ord_date, salesman_id FROM orders
WHERE salesman_id = (
    SELECT salesman_id FROM salesman
    WHERE commission = (
        SELECT MAX(commission) FROM salesman
    )
);
```

<br>
 
#### 10. From the following tables, write a SQL query to find the customers whose orders issued on 17th August, 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id and cust_name.

```sql
SELECT orders.ord_no, orders.purch_amt, orders.ord_date, orders.salesman_id, customer.cust_name FROM orders, customer
WHERE orders.customer_id = customer.customer_id
AND orders.ord_date = '2012-08-17';
```

<br>
 
#### 11. From the following tables, write a SQL query to find the salespeople who had more than one customer. Return salesman_id and name.

```sql
SELECT name, salesman_id FROM salesman
WHERE 1 < (
    SELECT COUNT(customer_id) FROM customer
    WHERE salesman.salesman_id = customer.salesman_id
);
```

<br>
 
#### ** 12. From the following tables, write a SQL query to find those orders, which amount is higher than the average amount of the related customer. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT * FROM orders a
WHERE purch_amt > (
    SELECT AVG(purch_amt) FROM orders b
    WHERE a.customer_id = b.customer_id
);
```

<br>
 
#### ** 13. From the following tables, write a SQL query to find those orders, which are equal or higher than average amount of the orders. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT * FROM orders a
WHERE purch_amt >= (
    SELECT AVG(purch_amt) FROM orders b
    WHERE a.customer_id = b.customer_id
);
```

<br>
 
#### 14. Write a query to find the sums of the amounts from the orders table, grouped by date, eliminating all those dates where the sum was not at least 1000.00 above the maximum order amount for that date. 

```sql
SELECT ord_date, SUM(purch_amt) from orders a
GROUP BY ord_date
HAVING SUM(purch_amt) > (
    SELECT MAX(purch_amt) + 1000 FROM orders b
    WHERE a.ord_date = b.ord_date
);
```

<br>
 
#### 15. Write a query to extract all data from the customer table if and only if one or more of the customers in the customer table are located in London. 

```sql
SELECT * FROM customer
WHERE 1 <= (
    SELECT COUNT(city) FROM customer
    WHERE city = 'London'
);
```

<br>
 
#### 16. From the following tables, write a SQL query to find the salespeople who deal multiple customers. Return salesman_id, name, city and commission.

```sql

```

<br>
 
#### 17. From the following tables, write a SQL query to find the salespeople who deal a single customer. Return salesman_id, name, city and commission.

```sql

```

<br>
 
#### 18. From the following tables, write a SQL query to find the salespeople who deal the customers with more than one order. Return salesman_id, name, city and commission.

```sql

```

<br>
 
#### 19. From the following tables, write a SQL query to find the salespeople who deals those customers who live in the same city. Return salesman_id, name, city and commission.

```sql

```

<br>
 
#### 20. From the following tables, write a SQL query to find the salespeople whose place of living (city) matches with any of the city where customers live. Return salesman_id, name, city and commission.

```sql

```

<br>
 
#### 21. From the following tables, write a SQL query to find all those salespeople whose name exist alphabetically after the customer’s name. Return salesman_id, name, city, commission.

```sql

```

<br>
 
#### 22. From the following table, write a SQL query to find all those customers who have a greater grade than any customer who belongs to the alphabetically lower than the city of New York. Return customer_id, cust_name, city, grade, salesman_id.

```sql

```

<br>
 
#### 23. From the following table, write a SQL query to find all those orders whose order amount greater than at least one of the orders of September 10th 2012. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql

```

<br>
 
#### 24. From the following tables, write a SQL query to find those orders where an order amount less than any order amount of a ..

```sql

```

<br>
 
#### 25. From the following tables, write a SQL query to find those orders where every order amount less than the maximum order amount of a customer lives in London City. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql

```

<br>
 
#### 26. From the following tables, write a SQL query to find those customers whose grade are higher than customers living in New York City. Return customer_id, cust_name, city, grade and salesman_id.

```sql

```

<br>
 
#### 27. From the following tables, write a SQL query to calculate the total order amount generated by a salesman. The salesman should belong to the cities where any of the customer living. Return salesman name, city and total order amount.

```sql

```

<br>
 
#### 28. From the following tables, write a SQL query to find those customers whose grade doesn't same of those customers live in London City. Return customer_id, cust_name, city, grade and salesman_id.

```sql

```

<br>
 
#### 29. From the following tables, write a SQL query to find those customers whose grade are not same of those customers living in Paris. Return customer_id, cust_name, city, grade and salesman_id.

```sql

```

<br>
 
#### 30. From the following tables, write a SQL query to find all those customers who have different grade than any customer lives in Dallas City. Return customer_id, cust_name,city, grade and salesman_id.

```sql

```

<br>
 
#### 31. From the following tables, write a SQL query to find the average price of each manufacturer's product along with their name. Return Average Price and Company.

```sql

```

<br>
 
#### 32. From the following tables, write a SQL query to calculate the average price of the products and find price which are more than or equal to 350. Return Average Price and Company.

```sql

```

<br>
 
#### 33. From the following tables, write a SQL query to find the most expensive product of each company. Return Product Name, Price and Company.

```sql

```

<br>
 
#### 34. From the following tables, write a SQL query to find those employees whose last name is 'Gabriel' or 'Dosio'. Return emp_idno, emp_fname, emp_lname and emp_dept.

```sql

```

<br>
 
#### 35. From the following tables, write a SQL query to find the employees who work in department 89 or 63. Return emp_idno, emp_fname, emp_lname and emp_dept.

```sql

```

<br>
 
#### 36. From the following tables, write a SQL query to find those employees who work for the department where the department allotment amount is more than Rs. 50000. Return emp_fname and emp_lname.

```sql

```

<br>
 
#### 37. From the following tables, write a SQL query to find the departments where the sanction amount is higher than the average sanction amount of all the departments. Return dpt_code, dpt_name and dpt_allotment.

```sql

```

<br>
 
#### 38. From the following tables, write a SQL query to find the departments where more than two employees work. Return dpt_name.

```sql

```

<br>
 
#### 39. From the following tables, write a SQL query to find the departments where the sanction amount is second lowest. Return emp_fname and emp_lname.

```sql

```

<br>
 
 ### FILTERING and SORTING 

#### 1. From the following table, write a SQL query to find those employees whose salary is less than 6000. Return full name (first and last name), and salary.

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full Name", salary FROM employees
WHERE salary < 6000;
```

<br>
 
#### 2. From the following table, write a SQL query to find those employees whose salary is higher than 8000. Return first name, last name and department number and salary. 

```sql
SELECT first_name, last_name, department_id, salary FROM employees
WHERE salary > 8000;
```

<br>
 
#### 3. From the following table, write a SQL query to find those employees whose last name is "McEwen". Return first name, last name and department ID. 

```sql
SELECT first_name, last_name, department_id FROM employees
WHERE last_name = 'McEwen';
```

<br>
 
#### 4. From the following table, write a SQL query to find those employees who have no department number. Return employee_id, first_name, last_name, email,phone_number,hire_date, job_id, salary,commission_pct,manager_id and department_id.

```sql
SELECT * FROM employees
WHERE department_id IS NULL;
```

<br>
 
#### 5. From the following table, write a SQL query to find the details of 'Marketing' department. Return all fields. 

```sql
SELECT * FROM departments
WHERE department_name = 'Marketing';
```

<br>
 
#### 6. From the following table, write a SQL query to find those employees whose first name does not contain the letter ‘M’. Sort the result-set in ascending order by department ID. Return full name (first and last name together), hire_date, salary and department_id. 

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full_Name", hire_date, salary, department_id FROM employees
WHERE first_name NOT LIKE '%M%'
ORDER BY department_id;
```

<br>
 
#### 7. From the following table, write a SQL query to find those employees who falls in the following criteria : 1. whose salary is in the range of 8000, 12000 (Begin and end values are included.) and get some commission. 2. : those employees who joined before ‘2003-06-05’ and not included in the department number 40, 120 and 70. Return all fields.

```sql
SELECT * FROM employees
WHERE (
    salary BETWEEN 8000 AND 12000 
    AND commission_pct IS NOT NULL
    )
OR (
    hire_date < '2003-06-05'
    AND department_id NOT IN (40, 120, 70)
);
```

<br>
 
#### 8. From the following table, write a SQL query to find those employees who do not earn any commission.Return full name (first and last name), and salary. 

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full_Name", salary FROM employees
WHERE commission_pct IS NULL;
```

<br>
 
#### 9. From the following table, write a SQL query to find those employees whose salary is in the range 9000,17000 (Begin and end values are included). Return full name, contact details and salary.

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full_Name",CONCAT(email, ' ', phone_number) AS "contact", salary FROM employees
WHERE salary BETWEEN 9000 AND 17000;
```

<br>
 
#### 10. From the following table, write a SQL query to find those employees whose first name ends with the letter ‘m’. Return the first and last name, and salary. 

```sql
SELECT first_name, last_name, salary FROM employees
WHERE first_name LIKE '%m';
```

<br>
 
#### 11. From the following table, write a SQL query to find those employees whose salary is not in the range 7000 and 15000 (Begin and end values are included). Sort the result-set in ascending order by the full name (first and last). Return full name and salary. 

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full_Name", salary FROM employees
WHERE salary NOT BETWEEN 7000 AND 15000
ORDER BY 1;
```

<br>
 
#### 12. From the following table, write a SQL query to find those employees who were hired during November 5th, 2007 and July 5th, 2009. Return full name (first and last), job id and hire date. 

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full_Name", job_id, hire_date FROM employees
WHERE hire_date BETWEEN '2007-11-05' AND '2009-07-05';
```

<br>
 
#### 13. From the following table, write a SQL query to find those employees who works either in department 70 or 90. Return full name (first and last name), department id.

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full_Name", department_id FROM employees
WHERE department_id = 70 or department_id = 90;
```

<br>
 
#### 14. From the following table, write a SQL query to find those employees who work under a manager. Return full name (first and last name), salary, and manager ID.

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full_Name", salary, manager_id FROM employees
WHERE manager_id IS NOT NULL;
```

<br>
 
#### 15. From the following table, write a SQL query to find those employees who were hired before June 21st, 2002. Return all fields. 

```sql
SELECT * FROM employees
WHERE hire_date < '2002-06-21';
```

<br>
 
#### 16 . From the following table, write a SQL query to find those employees whose managers hold the ID 120 or 103 or 145. Return first name, last name, email, salary and manager ID.

```sql
SELECT first_name, last_name, email, salary, manager_id FROM employees
WHERE manager_id in (120, 103, 145);
```

<br>
 
#### * 17. From the following table, write a SQL query to find those employees whose first name contains the letters D, S, or N. Sort the result-set in descending order by salary. Return all fields.

```sql
SELECT * FROM employees
WHERE first_name SIMILAR TO '%[D,S,N]%'
ORDER BY salary DESC;
```

<br>
 
#### 18. From the following table, write a SQL query to find those employees who earn above 11000 or the seventh character in their phone number is 3. Sort the result-set in descending order by first name. Return full name (first name and last name), hire date, commission percentage, email, and telephone separated by '-', and salary. 

```sql
SELECT CONCAT(first_name, ' ', last_name) AS "Full_Name", hire_date, commission_pct, CONCAT(email, ' - ', phone_number) AS "contact", salary FROM employees
WHERE salary > 11000
OR phone_number LIKE '______3%'
ORDER BY first_name DESC;
```

<br>
 
#### 19. From the following table, write a SQL query to find those employees whose first name contains a character ‘s’ in 3rd position. Return first name, last name and department id.

```sql
SELECT first_name, last_name, department_id FROM employees
WHERE first_name LIKE '__s%';
```

<br>
 
#### 20. From the following table, write a SQL query to find those employees who are working in the departments, which are not included in the department number 50 or 30 or 80. Return employee_id, first_name, job_id, department_id. 

```sql
SELECT employee_id, first_name, job_id, department_id FROM employees
WHERE department_id NOT IN (50, 30, 80);
```

<br>
 
#### 21. From the following table, write a SQL query to find those employees whose department numbers are included in 30 or 40 or 90. Return employee id, first name, job id, department id. 

```sql
SELECT employee_id, first_name, job_id, department_id FROM employees
WHERE department_id IN (30, 40, 90);
```

<br>
 
#### 22. From the following table, write a SQL query to find those employees who worked more than two jobs in the past. Return employee id.

```sql
SELECT employee_id FROM job_history
GROUP BY employee_id
HAVING COUNT(employee_id) >= 2;
```

<br>
 
#### 23. From the following table, write a SQL query to count the number of employees, sum of all salary, and difference between the highest salary and lowest salary by each job id. Return job_id, count, sum, salary_difference.

```sql
SELECT job_id, COUNT(*), SUM(salary), MAX(salary) - MIN(salary) AS "salary_difference" FROM employees
GROUP BY job_id;
```

<br>
 
#### 24. From the following table, write a SQL query to find each job ids where two or more employees worked for more than 300 days. Return job id.

```sql
SELECT job_id FROM job_history
WHERE end_date - start_date > 300
GROUP BY job_id
HAVING COUNT(*) >= 2;
```

<br>
 
#### 25. From the following table, write a SQL query to count the number of cities in each country has. Return country ID and number of cities.

```sql
SELECT country_id, COUNT(city) FROM locations
GROUP BY country_id;
```

<br>
 
#### 26. From the following table, write a SQL query to count the number of employees worked under each manager. Return manager ID and number of employees.

```sql
SELECT manager_id, COUNT(employee_id) FROM employees
GROUP BY manager_id;
```

<br>
 
#### 27. From the following table, write a SQL query to find all jobs. Sort the result-set in descending order by job title. Return all fields. 

```sql
SELECT * FROM jobs
ORDER BY job_title DESC;
```

<br>
 
#### 28. From the following table, write a SQL query to find all those employees who are either Sales Representative or Salesman. Return first name, last name and hire date.

```sql
SELECT first_name, last_name, hire_date FROM employees
WHERE job_id IN ('SA_REP', 'SA_MAN');
```

<br>
 
#### 29. From the following table, write a SQL query to calculate average salary of those employees for each department who get a commission percentage. Return department id, average salary.

```sql
SELECT department_id, AVG(salary) FROM employees
WHERE commission_pct IS NOT NULL
GROUP BY department_id;
```

<br>
 
#### 30. From the following table, write a SQL query to find those departments where a manager can manage four or more employees. Return department_id.

```sql
SELECT DISTINCT department_id FROM employees
GROUP BY department_id, manager_id
HAVING COUNT(employee_id) >= 4;
```

<br>
 
#### 31. From the following table, write a SQL query to find those departments where more than ten employees work, who got a commission percentage. Return department id. 

```sql
SELECT DISTINCT department_id FROM employees
WHERE commission_pct IS NOT NULL
GROUP BY department_id
HAVING COUNT(employee_id) >= 10;
```

<br>
 
#### * 32. From the following table, write a SQL query to find those employees who have completed their previous jobs. Return employee ID, end_date. 

```sql
SELECT employee_id, MAX(end_date) FROM job_history
GROUP BY employee_id
HAVING COUNT(employee_id) > 1;
```

<br>
 
#### 33. From the following table, write a SQL query to find those employees who have no commission percentage and salary within the range 7000, 12000 (Begin and end values are included.) and works in the department number 50. Return all the fields of employees.

```sql
SELECT * FROM employees
WHERE commission_pct IS NULL
AND salary BETWEEN 7000 AND 12000
AND department_id = 50;
```

<br>
 
#### 34. From the following table, write a SQL query to compute the average salary of each job ID. Exclude those records where average salary is higher than 8000. Return job ID, average salary.

```sql
SELECT job_id, AVG(salary) FROM employees
GROUP BY job_id
HAVING AVG(salary) <= 8000;
```

<br>
 
#### 35. From the following table, write a SQL query to find those job titles where the difference between minimum and maximum salaries is in the range the range 12000, 18000 (Begin and end values are included.). Return job_title, max_salary-min_salary. 

```sql
SELECT job_title, max_salary - min_salary AS "Salary Difference" FROM jobs
WHERE max_salary - min_salary BETWEEN 12000 AND 18000;
```

<br>
 
#### 36. From the following table, write a SQL query to find those employees whose first name or last name starts with the letter ‘D’. Return first name, last name. 

```sql
SELECT first_name, last_name FROM employees
WHERE first_name LIKE 'D%'
OR last_name LIKE 'D%';
```

<br>
 
#### 37. From the following table, write a SQL query to find details of those jobs where minimum salary exceeds 9000. Return all the fields of jobs.

```sql
SELECT * FROM jobs
WHERE min_salary > 9000;
```

<br>
 
#### 38. From the following table, write a SQL query to find those employees who joined after 7th September 1987. Return all the fields. 

```sql
SELECT * FROM employees
WHERE hire_date > '1987-09-07';
```

<br>
 
### SQL JOINS

#### 1. From the following tables, write a SQL query to find the first name, last name, department number, and department name for each employee. 

```sql
SELECT employees.first_name, employees.last_name, employees.department_id, departments.department_name FROM employees
JOIN departments ON employees.department_id = departments.department_id;
```

<br>
 
#### 2. From the following tables, write a SQL query to find the first name, last name, department, city, and state province for each employee.

```sql
SELECT employees.first_name, employees.last_name, departments.department_name, locations.city, locations.state_province FROM employees
JOIN departments ON employees.department_id = departments.department_id
JOIN locations ON departments.location_id = locations.location_id;
```

<br>
 
#### 3. From the following table, write a SQL query to find the first name, last name, salary, and job grade for all employees. 

```sql
SELECT employees.first_name, employees.last_name, employees.salary, job_grades.grade_level FROM employees, job_grades
WHERE employees.salary BETWEEN job_grades.lowest_sal AND job_grades.highest_sal;
```

<br>
 
#### 4. From the following tables, write a SQL query to find all those employees who work in department ID 80 or 40. Return first name, last name, department number and department name.

```sql
SELECT employees.first_name, employees.last_name, departments.department_id, departments.department_name FROM employees, departments
WHERE employees.department_id = departments.department_id
AND departments.department_id IN (80, 40);
```

<br>
 
#### 5. From the following tables, write a SQL query to find those employees whose first name contains a letter ‘z’. Return first name, last name, department, city, and state province.

```sql
SELECT employees.first_name, employees.last_name, departments.department_name, locations.city, locations.state_province FROM employees
JOIN departments ON employees.department_id = departments.department_id
JOIN locations ON departments.location_id = locations.location_id
WHERE employees.first_name LIKE '%z%';
```

<br>
 
#### 6. From the following table, write a SQL query to find all departments including those without any employee. Return first name, last name, department ID, department name.

```sql
SELECT employees.first_name, employees.last_name, departments.department_id, departments.department_name FROM employees
RIGHT JOIN departments ON employees.department_id = departments.department_id;
```

<br>
 
#### 7. From the following table, write a SQL query to find those employees who earn less than the employee of ID 182. Return first name, last name and salary. 

```sql
SELECT employees.first_name, employees.last_name,employees.salary FROM employees
WHERE employees.salary < (
    SELECT employees.salary FROM employees
    WHERE employees.employee_id = 182
);
```

<br>
 
#### * 8. From the following table, write a SQL query to find the employees and their managers. Return the first name of the employee and manager. 

```sql
SELECT emp.first_name, mng.first_name AS "test" FROM employees emp
JOIN employees mng ON emp.manager_id = mng.employee_id;
```

<br>
 
#### 9. From the following tables, write a SQL query to display the department name, city, and state province for each department.

```sql
SELECT departments.department_name, locations.city, locations.state_province FROM departments
JOIN locations ON departments.location_id = locations.location_id;
```

<br>
 
#### 10. From the following tables, write a SQL query to find those employees who have or not any department. Return first name, last name, department ID, department name.

```sql
SELECT employees.first_name, employees.last_name, employees.department_id, departments.department_name FROM employees
LEFT JOIN departments ON employees.department_id = departments.department_id;
```

<br>
 
#### 11. From the following table, write a SQL query to find the employees and their managers. These managers do not work under any manager. Return the first name of the employee and manager.

```sql
SELECT emp.first_name AS "Employee", mng.first_name AS "Manager" FROM employees emp
LEFT JOIN employees mng ON emp.manager_id = mng.employee_id;
```

<br>
 
#### 12. From the following tables, write a SQL query to find those employees who work in a department where the employee of last name 'Taylor' works. Return first name, last name and department ID.

```sql
SELECT emp.first_name, emp.last_name, tlr.department_id FROM employees emp
LEFT JOIN employees tlr ON emp.department_id = tlr.department_id
WHERE tlr.last_name = 'Taylor';
```

<br>
 
#### ** 13. From the following tables, write a SQL query to find those employees who joined on 1st January 1993 and leave on or before 31 August 1997. Return job title, department name, employee name, and joining date of the job. 

```sql
SELECT jobs.job_title, departments.department_name, CONCAT(employees.first_name, ' ', employees.last_name) AS "Employee Name", job_history.start_date FROM jobs
JOIN job_history ON jobs.job_id = job_history.job_id
JOIN employees ON jobs.job_id = employees.job_id
JOIN departments ON employees.department_id = departments.department_id
WHERE job_history.start_date >= '1993-01-01'
AND job_history.start_date <= '1997-08-31';
```

<br>
 
#### * 14. From the following tables, write a SQL query to find the difference between maximum salary of the job and salary of the employees. Return job title, employee name, and salary difference.

```sql
SELECT jobs.job_title, employees.first_name, (jobs.max_salary - employees.salary) AS "Salary Difference" FROM jobs
JOIN employees USING (job_id);
```

<br>
 
#### 15. From the following table, write a SQL query to compute the average salary, number of employees received commission in that department. Return department name, average salary and number of employees.

```sql
SELECT departments.department_name, AVG(employees.salary), COUNT(employees.employee_id) FROM employees
JOIN departments USING (department_id)
GROUP BY departments.department_id;
```

<br>
 
#### 16. From the following tables, write a SQL query to compute the difference between maximum salary and salary of all the employees who works the department of ID 80. Return job title, employee name and salary difference.

```sql
SELECT jobs.job_title, employees.first_name, jobs.max_salary - employees.salary AS "Salary Difference" FROM jobs
JOIN employees USING(job_id)
WHERE employees.department_id = 80;
```

<br>
 
#### 17. From the following table, write a SQL query to find the name of the country, city, and departments, which are running there.

```sql
SELECT countries.country_name, locations.city, departments.department_name FROM countries
JOIN locations USING (country_id)
JOIN departments USING(location_id);
```

<br>
 
#### 18. From the following tables, write a SQL query to find the department name and the full name (first and last name) of the manager.

```sql
SELECT departments.department_name, employees.first_name, employees.last_name FROM departments
JOIN employees ON employees.employee_id = departments.manager_id;
```

<br>
 
#### 19. From the following table, write a SQL query to compute the average salary of employees for each job title. 

```sql
SELECT AVG(employees.salary), jobs.job_title FROM employees
JOIN jobs ON employees.job_id = jobs.job_id
GROUP BY jobs.job_title;
```

<br>
 
#### 20. From the following table, write a SQL query to find those employees who earn $12000 and above. Return employee ID, starting date, end date, job ID and department ID. 

```sql
SELECT employees.employee_id, job_history.start_date, job_history.end_Date, job_history.job_id, job_history.department_id FROM employees
JOIN job_history USING (employee_id)
WHERE employees.salary >= 12000;
```

<br>
 
#### ** 21. From the following tables, write a SQL query to find those departments where at least 2 employees work. Group the result set on country name and city. Return country name, city, and number of departments. 

```sql
SELECT countries.country_name, locations.city, COUNT(departments.department_id) FROM countries
JOIN locations USING (country_id)
JOIN departments USING (location_id)
WHERE departments.department_id IN (
    SELECT department_id FROM employees
    GROUP BY department_id
    HAVING COUNT(department_id) >= 2
)
GROUP BY countries.country_name, locations.city;
```

<br>
 
#### 22. From the following tables, write a SQL query to find the department name, full name (first and last name) of the manager and their city. 

```sql
SELECT departments.department_name, CONCAT(employees.first_name, ' ', employees.last_name) AS "Full Name", locations.city FROM departments
JOIN employees ON departments.manager_id = employees.employee_id
JOIN locations USING (location_id); 
```

<br>
 
#### 23. From the following tables, write a SQL query to compute the number of days worked by employees in a department of ID 80. Return employee ID, job title, number of days worked.

```sql
SELECT job_history.employee_id, jobs.job_title, (job_history.end_date - job_history.start_date) AS "Work Days" FROM job_history
JOIN jobs USING (job_id)
WHERE job_history.department_id = 80;
```

<br>
 
#### 24. From the following tables, write a SQL query to find full name (first and last name), and salary of those employees who work in any department located in 'London' city.

```sql
SELECT CONCAT(employees.first_name, ' ', employees.last_name) AS "Full Name", employees.salary FROM employees
JOIN departments USING (department_id)
JOIN locations ON departments.location_id = locations.location_id 
AND locations.city = 'London';
```

<br>
 
#### ** 25. From the following tables, write a SQL query to find full name (first and last name), job title, starting and ending date of last jobs of employees who worked without a commission percentage.

```sql
SELECT CONCAT(e.first_name, ' ', e.last_name) AS "Full Name", j.job_title FROM employees e
JOIN (
    SELECT MAX(start_date), MAX(end_date), employee_id FROM job_history
    GROUP BY employee_id
    ) h 
    ON e.employee_id=h.employee_id
    JOIN jobs j ON j.job_id=e.job_id
    WHERE e.commission_pct = 0;
```

<br>
 
#### 26. From the following tables, write a SQL query to find the department name, department ID, and number of employees in each department.

```sql
SELECT departments.department_name, departments.department_id, COUNT(employees.employee_id) FROM departments
JOIN employees USING (department_id)
GROUP BY department_id;
```

<br>
 
#### 27. From the following tables, write a SQL query to find the full name (first and last name) of the employee with ID and name of the country presently where he/she is working. 

```sql
SELECT CONCAT(employees.first_name, ' ', employees.last_name), employees.employee_id, countries.country_name FROM employees
JOIN departments USING (department_id)
JOIN locations USING (location_id)
JOIN countries USING (country_id);
```

<br>
 