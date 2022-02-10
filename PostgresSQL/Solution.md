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
