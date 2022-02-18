# Exercises Solution (MySQL)

## Setup

- Follow this [guide](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database) to install PostgresSQL on WSL2.

- Install  [MySQL](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2) Extension on `VSCode`.

- Run the command `$ sudo service postgresql start`.

- Run the command `$ sudo -u postgres psql`.

- Create a new connection with the extension, using the credentials you created while installing PostgreSQL earlier. Make sure you choose server type as `PostgresSQL`.

- In Postgres Shell, create a new Database `# create database "LearnSQL"`.

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