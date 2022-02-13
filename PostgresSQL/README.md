# [SQL Exercises, Practice, Solution - Retrieve data from tables](https://www.w3resource.com/sql-exercises/sql-retrieve-from-table.php)

## Retrieve data from tables

1. Write a SQL statement to display all the information of all salesmen.
2. Write a SQL statement to display a string "This is SQL Exercise, Practice and Solution".
3. Write a query to display three numbers in three columns.
4. Write a query to display the sum of two numbers 10 and 15 from RDMS sever.
5. Write a query to display the result of an arithmetic expression.
6. Write a SQL statement to display specific columns like name and commission for all the salesmen.
7. Write a query to display the columns in a specific order like order date, salesman id, order number and purchase amount from for all the orders.
8. From the following table, write a SQL query to find the unique salespeople ID. Return salesman_id.
9. From the following table, write a SQL query to find the salespeople who lives in the City of 'Paris'. Return salesperson's name, city.
10. From the following table, write a SQL query to find those customers whose grade is 200. Return customer_id, cust_name, city, grade, salesman_id.
11. From the following table, write a SQL query to find the orders, which are delivered by a salesperson of ID. 5001. Return ord_no, ord_date, purch_amt.
12. From the following table, write a SQL query to find the Nobel Prize winner(s) in the year 1970. Return year, subject and winner.
13. From the following table, write a SQL query to find the Nobel Prize winner in 'Literature' in the year 1971. Return winner.
14. From the following table, write a SQL query to find the Nobel Prize winner 'Dennis Gabor'. Return year, subject.
15. From the following table, write a SQL query to find the Nobel Prize winners in 'Physics' since the year 1950. Return winner.
16. From the following table, write a SQL query to find the Nobel Prize winners in 'Chemistry' between the years 1965 to 1975. Begin and end values are included. Return year, subject, winner, and country.
17. Write a SQL query to show all details of the Prime Ministerial winners after 1972 of Menachem Begin and Yitzhak Rabin.
18. From the following table, write a SQL query to find the details of the winners whose first name matches with the string 'Louis'. Return year, subject, winner, country, and category.
19. From the following table, write a SQL query to combine the winners in Physics, 1970 and in Economics, 1971. Return year, subject, winner, country, and category.
20. From the following table, write a SQL query to find the Nobel Prize winners in 1970 excluding the subjects Physiology and Economics. Return year, subject, winner, country, and category.
21. From the following table, write a SQL query to combine the winners in 'Physiology' before 1971 and winners in 'Peace' on or after 1974. Return year, subject, winner, country, and category.
22. From the following table, write a SQL query to find the details of the Nobel Prize winner 'Johannes Georg Bednorz'. Return year, subject, winner, country, and category.
23. From the following table, write a SQL query to find the Nobel Prize winners for the subject not started with the letter 'P'. Return year, subject, winner, country, and category. Order the result by year, descending.
24. From the following table, write a SQL query to find the details of 1970 Nobel Prize winners. Order the result by subject, ascending except ‘Chemistry’ and ‘Economics’ which will come at the end of result set. Return year, subject, winner, country, and category.
25. From the following table, write a SQL query to select a range of products whose price is in the range Rs.200 to Rs.600. Begin and end values are included. Return pro_id, pro_name, pro_price, and pro_com.
26. From the following table, write a SQL query to calculate the average price for manufacturer code equal to 16. Return avg.
27. From the following table, write a SQL query to display the pro_name as 'Item Name' and pro_priceas 'Price in Rs.' 
28. From the following table, write a SQL query to find the items whose prices are higher than or equal to $250. Order the result by product price in descending, then product name in ascending. Return pro_name and pro_price.
29. From the following table, write a SQL query to calculate average price of the items of each company. Return average price and company code.
30. From the following table, write a SQL query to find the cheapest item(s). Return pro_name and, pro_price.
31. From the following table, write a SQL query to find unique last name of all employees. Return emp_lname.
32. From the following table, write a SQL query to find the details of employees whose last name is 'Snares'. Return emp_idno, emp_fname, emp_lname, and emp_dept.
33. From the following table, write a SQL query to find the details of the employees who work in the department 57. Return emp_idno, emp_fname, emp_lname and emp_dept.

## Boolean and Relational Operators

1. From the following table, write a SQL query to find the details of the customers who have a gradevalue above 100. Return customer_id, cust_name, city, grade, and salesman_id.
2. From the following table, write a SQL query to find all the customers in ‘New York’ city who have a grade value above 100. Return customer_id, cust_name, city, grade, and salesman_id.
3. From the following table, write a SQL query to find the customers who belong to either the city ‘New York’ or have a grade above 100. Return customer_id, cust_name, city, grade, and salesman_id.
4. From the following table, write a SQL query to find the customers who belong to either the city ‘New York’ or not have a grade above 100. Return customer_id, cust_name, city, grade, and salesman_id.
5. From the following table, write a SQL query to find those customers who belong to neither the ‘New York’ city nor their grade value exceeds 100. Return customer_id, cust_name, city, grade, and salesman_id.
6. From the following table, write a SQL query to find details of all order excluding combination of ord_date equal to '2012-09-10' and salesman_id higher than 5005 or purch_amt greater than 1000. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
7. From the following table, write a SQL query to find the details of those salespeople whose commissions range from 0.10 to0.12. Return salesman_id, name, city, and commission.
8. From the following table, write a SQL query to find details of all order where purchase amount less than 200 or excluding combination of order date greater than or equal to '2012-02-10' and customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
9. From the following table, write a SQL query to find all orders subject to following conditions. Exclude combination of order date equal to '2012-08-17' or customer ID higher than 3005 and purchase amount less than 1000.
10. Write a SQL query to display order number, purchase amount, achieved, the unachieved percentage for those order which exceeds the 50% of the target value of 6000. 
11. From the following table, write a SQL query to find the details of all employees whose last name is ‘Dosni’ or ‘Mardy’. Return emp_idno, emp_fname, emp_lname, and emp_dept.
12. From the following table, write a SQL query to find the employees who works at depart 47 or 63. Return emp_idno, emp_fname, emp_lname, and emp_dept.