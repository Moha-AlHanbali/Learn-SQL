# [SQL Exercises, Practice, Solution - Retrieve data from tables](https://www.w3resource.com/sql-exercises/)

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

## Wildcard and Special operators

1. From the following table, write a SQL query to find the details of those salespeople who come from the 'Paris' City or 'Rome' City. Return salesman_id, name, city, commission.
2. From the following table, write a SQL query to find the details of those salespeople who come from any of the City 'Paris' or 'Rome'. Return salesman_id, name, city, commission.
3. From the following table, write a SQL query to find the details of those salespeople who live in cities apart from 'Paris' and 'Rome'. Return salesman_id, name, city, commission. 
4. From the following table, write a SQL query to find the details of the customers whose ID belongs to any of the values 3007, 3008 and 3009. Return customer_id, cust_name, city, grade, and salesman_id.
5. From the following table, write a SQL query to find the details of salespeople who get the commission in the range from 0.12 to 0.14 (begin and end values are included). Return salesman_id, name, city, and commission. 
6. From the following table, write a SQL query to select orders value within a range 500, 4000 (begin and end values are included). Exclude orders amount 948.50 and 1983.43. Return ord_no, purch_amt, ord_date, customer_id, and salesman_id.
7. From the following table, write a SQL query to find the details of those salespeople whose name starts with any letter within 'A' and 'L' (not inclusive). Return salesman_id, name, city, commission. 
8. From the following table, write a SQL query to find the details of all salespeople except whose name starts with any letter within 'A' and 'L' (not inclusive). Return salesman_id, name, city, commission.
9. From the following table, write a SQL query to find the details of the customers whose name begins with the letter 'B'. Return customer_id, cust_name, city, grade, salesman_id.
10. From the following table, write a SQL query to find the details of the customers whose names end with the letter 'n'. Return customer_id, cust_name, city, grade, salesman_id.
11. From the following table, write a SQL query to find the details of those salespeople whose name starts with ‘N’ and the fourth character is 'l'. Rests may be any character. Return salesman_id, name, city, commission. 
12. From the following table, write a SQL query to find those rows where col1 contains the escape character underscore ( _ ). Return col1.
13. From the following table, write a SQL query to find those rows where col1 does not contain the escape character underscore ( _ ). Return col1. 
14. From the following table, write a SQL query to find those rows where col1 contains the forward slash character ( / ). Return col1. 
15. From the following table, write a SQL query to find those rows where col1 does not contain the forward slash character ( / ). Return col1.
16. From the following table, write a SQL query to find those rows where col1 contains the string ( _/ ). Return col1. 
17. From the following table, write a SQL query to find those rows where col1 does not contain the string ( _/ ). Return col1. 
18. From the following table, write a SQL query to find those rows where col1 contains the character percent ( % ). Return col1.
19. From the following table, write a SQL query to find those rows where col1 does not contain the character percent ( % ). Return col1.
20. From the following table, write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id. 
21. From the following table, write a SQL query to find all those customers whose grade value exists. Return customer_id, cust_name, city, grade, salesman_id.
22. From the following table, write a SQL query to find the employees whose last name begins with the character 'D'. Return emp_idno, emp_fname, emp_lname and emp_dept.

## Aggregate Functions

1. From the following table, write a SQL query to calculate total purchase amount of all orders. Return total purchase amount. 
2. From the following table, write a SQL query to calculate average purchase amount of all orders. Return average purchase amount. 
3. From the following table, write a SQL query to count the number of unique salespeople. Return number of salespeople. 
4. From the following table, write a SQL query to count the number of customers. Return number of customers. 
5. From the following table, write a SQL query to find the number of customers who got at least a gradation for his/her activity.
6. From the following table, write a SQL query to find the maximum purchase amount.
7. From the following table, write a SQL query to find the minimum purchase amount.
8. From the following table, write a SQL query to find the highest grade of the customers for each of the city. Return city, maximum grade.
9. From the following table, write a SQL query to find the highest purchase amount ordered by each customer. Return customer ID, maximum purchase amount.
10. From the following table, write a SQL query to find the highest purchase amount ordered by each customer on a particular date. Return, order date and highest purchase amount.
11. From the following table, write a SQL query to find the highest purchase amount on '2012-08-17' by each salesperson. Return salesperson ID, purchase amount.
12. From the following table, write a SQL query to find highest order (purchase) amount by each customer in a particular order date. Filter the result by highest order (purchase) amount above 2000.00. Return customer id, order date and maximum purchase amount. 
13. From the following table, write a SQL query to find the maximum order (purchase) amount in the range 2000, 6000 (Begin and end values are included.) by combination of each customer and order date. Return customer id, order date and maximum purchase amount.
14. From the following table, write a SQL query to find the maximum order (purchase) amount by the combination of each customer and order date. Filter the rows for maximum order (purchase) amount is either 2000, 3000, 5760, 6000. Return customer id, order date and maximum purchase amount. 
15. From the following table, write a SQL query to find the maximum order (purchase) amount by each customer. The customer ID should be in the range 3002 and 3007(Begin and end values are included.). Return customer id and maximum purchase amount. 
16. From the following table, write a SQL query to find the maximum order (purchase) amount for each customer. The customer ID should be in the range 3002 and 3007(Begin and end values are included.). Filter the rows for maximum order (purchase) amount is higher than 1000. Return customer id and maximum purchase amount.
17. From the following table, write a SQL query to find the maximum order (purchase) amount generated by each salesperson. Filter the rows for the salesperson ID is in the range 5003 and 5008 (Begin and end values are included.). Return salesperson id and maximum purchase amount.
18. From the following table, write a SQL query to count all the orders generated on '2012-08-17'. Return number of orders. 
19. From the following table, write a SQL query to count number of salespeople who belongs to a city. Return number of salespeople. 
20. From the following table, write a SQL query to count number of orders by the combination of each order date and salesperson. Return order date, salesperson id.
21. From the following table, write a SQL query to calculate the average product price. Return average product price. 
22. From the following table, write a SQL query to count number of products where product price is higher than or equal to 350. Return number of products.
23. From the following table, write a SQL query to compute the average price for unique companies. Return average price and company id.
24. From the following table, write a SQL query to compute the sum of the allotment amount of all departments. Return sum of the allotment amount. 
25. From the following table, write a SQL query to find the number of employees in each department. Return department code and number of employees

## Formatting query output

1. From the following table, write a SQL query to select all the salespeople. Return salesman_id, name, city, commission with the percent sign (%).
2. From the following table, write a SQL query to find the number of orders booked for each day. Return the result in a format like "For 2001-10-10 there are 15 orders".".
3. From the following table, write a SQL query to find all the orders. Sort the result-set in ascending order by ord_no. Return all fields.
4. From the following table, write a SQL query to find all the orders. Sort the result-set in descending order by ord_date. Return all fields.
5. From the following table, write a SQL query to find all the orders. Sort the result-set in descending order by ord_date and purch_amt. Return all fields.
6. From the following table, write a SQL query to find all the customers. Sort the result-set by customer_id. Return cust_name, city, grade.
7. From the following table, write a SQL query to calculate the maximum purchase amount generated by each sales person for every order date. Sort the result-set by sales person id and order date in ascending order. Return sales person id, order date and maximum purchase amount.
8. From the following table, write a SQL query to find all the customers. Sort the result-set in descending order on 3rd field. Return customer name, city and grade. 
9. From the following table, write a SQL query to count the unique orders, highest purchase amount for each customer. Sort the result-set in descending order on 2nd field. Return customer ID, number of distinct orders and highest purchase amount by each customer. 
10. From the following table, write a SQL query to calculate summation of purchase amount, total commission (15% for all salesmen) by each order date. Sort the result-set on order date. Return order date, summation of purchase amount and commission. 

## Query on Multiple Tables

1. From the following tables, write a SQL query to find the salespersons and customers who live in same city. Return customer name, salesperson name and salesperson city.
2. From the following tables, write a SQL query to find all the customers along with the salesperson who works for them. Return customer name, and salesperson name.
3. From the following tables, write a SQL query to find those sales people who generated orders for their customers but not located in the same city. Return ord_no, cust_name, customer_id (orders table), salesman_id (orders table).
4. From the following tables, write a SQL query to find those orders made by customers. Return order number, customer name. 
5. From the following tables, write a SQL query to find those customers where each customer has a grade and served by at least a salesperson who belongs to a city. Return cust_name as "Customer", grade as "Grade" and order_no as "Order No.".
6. From the following table, write a SQL query to find those customers who served by a salesperson and the salesperson works at the commission in the range 12% to 14% (Begin and end values are included.). Return cust_name AS "Customer", city AS "City".
7. From the following tables, write a SQL query to find those orders executed by the salesperson, ordered by the customer whose grade is greater than or equal to 200. Compute purch_amt*commission as "Commission". Return customer name, commission as "Commission%" and Commission.
8. From the following table, write a SQL query to find those customers who made orders on October 5, 2012. Return customer_id, cust_name, city, grade, salesman_id, ord_no, purch_amt, ord_date, customer_id and salesman_id.

## SQL JOINS

1. From the following tables write a SQL query to find the salesperson and customer who belongs to same city. Return Salesman, cust_name and city.
2. From the following tables write a SQL query to find those orders where order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.
3. From the following tables write a SQL query to find the salesperson(s) and the customer(s) he handle. Return Customer Name, city, Salesman, commission.
4. From the following tables write a SQL query to find those salespersons who received a commission from the company more than 12%. Return Customer Name, customer city, Salesman, commission.
5. From the following tables write a SQL query to find those salespersons do not live in the same city where their customers live and received a commission from the company more than 12%. Return Customer Name, customer city, Salesman, salesman city, commission. 
6. From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission.
7. Write a SQL statement to make a join on the tables salesman, customer and orders in such a form that the same column of each table will appear once and only the relational rows will come.
8. From the following tables write a SQL query to display the cust_name, customer city, grade, Salesman, salesman city. The result should be ordered by ascending on customer_id.
9. From the following tables write a SQL query to find those customers whose grade less than 300. Return cust_name, customer city, grade, Salesman, saleman city. The result should be ordered by ascending customer_id.
10. Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to find that either any of the existing customers have placed no order or placed one or more orders.
11. Write a SQL statement to make a report with customer name, city, order number, order date, order amount salesman name and commission to find that either any of the existing customers have placed no order or placed one or more orders by their salesman or by own.
12. Write a SQL statement to make a list in ascending order for the salesmen who works either for one or more customer or not yet join under any of the customers.
13. From the following tables write a SQL query to list all salespersons along with customer name, city, grade, order number, date, and amount.
14. Write a SQL statement to make a list for the salesmen who either work for one or more customers or yet to join any of the customer. The customer may have placed, either one or more orders on or above order amount 2000 and must have a grade, or he may not have placed any order to the associated supplier. 
15. Write a SQL statement to make a report with customer name, city, order no. order date, purchase amount for those customers from the existing list who placed one or more orders or which order(s) have been placed by the customer who is not on the list. 
16. Write a SQL statement to make a report with customer name, city, order no. order date, purchase amount for only those customers on the list who must have a grade and placed one or more orders or which order(s) have been placed by the customer who is neither in the list nor have a grade.
17. Write a SQL query to combine each row of salesman table with each row of customer table. 
18. Write a SQL statement to make a cartesian product between salesman and customer i.e. each salesman will appear for all customer and vice versa for that salesman who belongs to a city. 
19. Write a SQL statement to make a cartesian product between salesman and customer i.e. each salesman will appear for all customer and vice versa for those salesmen who belongs to a city and the customers who must have a grade. 
20. Write a SQL statement to make a cartesian product between salesman and customer i.e. each salesman will appear for all customer and vice versa for those salesmen who must belong a city which is not the same as his customer and the customers should have an own grade.
21. From the following tables write a SQL query to select all rows from both participating tables as long as there is a match between pro_com and com_id.
22. Write a SQL query to display the item name, price, and company name of all the products. 
23. From the following tables write a SQL query to calculate the average price of items of each company. Return average value and company name.
24. From the following tables write a SQL query to calculate and find the average price of items of each company higher than or equal to Rs. 350. Return average value and company name.
25. From the following tables write a SQL query to find the most expensive product of each company. Return pro_name, pro_price and com_name.
26. From the following tables write a SQL query to display all the data of employees including their department. 
27. From the following tables write a SQL to display the first name and last name of each employee, along with the name and sanction amount for their department.
28. From the following tables write a SQL query to find the departments with a budget more than Rs. 50000 and display the first name and last name of employees.
29. From the following tables write a SQL query to find the names of departments where more than two employees are working. Return dpt_name.

## SUBQUERIES

1. From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
2. From the following tables, write a SQL query to find all the orders, which are generated by those salespeople, who live in the city of London.Return ord_no, purch_amt, ord_date, customer_id, salesman_id.
3. From the following tables, write a SQL query to find the orders generated by the salespeople who works for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id. A customer can works only with a salespeople.
4. From the following tables, write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id. 
5. From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
6. From the following tables, write a SQL query to find the commission of the salespeople work in Paris City. Return commission.
7. Write a query to display all the customers whose id is 2001 bellow the salesman ID of Mc Lyon.
8. From the following tables, write a SQL query to count number of customers with grades above the average grades of New York City. Return grade and count.
9. From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.
10. From the following tables, write a SQL query to find the customers whose orders issued on 17th August, 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id and cust_name.
11. From the following tables, write a SQL query to find the salespeople who had more than one customer. Return salesman_id and name.
12. From the following tables, write a SQL query to find those orders, which amount is higher than the average amount of the related customer. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
13. From the following tables, write a SQL query to find those orders, which are equal or higher than average amount of the orders. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
14. Write a query to find the sums of the amounts from the orders table, grouped by date, eliminating all those dates where the sum was not at least 1000.00 above the maximum order amount for that date. 
15. Write a query to extract all data from the customer table if and only if one or more of the customers in the customer table are located in London. 
16. From the following tables, write a SQL query to find the salespeople who deal multiple customers. Return salesman_id, name, city and commission.
17. From the following tables, write a SQL query to find the salespeople who deal a single customer. Return salesman_id, name, city and commission.
18. From the following tables, write a SQL query to find the salespeople who deal the customers with more than one order. Return salesman_id, name, city and commission.
19. From the following tables, write a SQL query to find the salespeople who deals those customers who live in the same city. Return salesman_id, name, city and commission.
20. From the following tables, write a SQL query to find the salespeople whose place of living (city) matches with any of the city where customers live. Return salesman_id, name, city and commission.
21. From the following tables, write a SQL query to find all those salespeople whose name exist alphabetically after the customer’s name. Return salesman_id, name, city, commission.
22. From the following table, write a SQL query to find all those customers who have a greater grade than any customer who belongs to the alphabetically lower than the city of New York. Return customer_id, cust_name, city, grade, salesman_id.
23. From the following table, write a SQL query to find all those orders whose order amount greater than at least one of the orders of September 10th 2012. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
24. From the following tables, write a SQL query to find those orders where an order amount less than any order amount of a customer lives in London City. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
25. From the following tables, write a SQL query to find those orders where every order amount less than the maximum order amount of a customer lives in London City. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
26. From the following tables, write a SQL query to find those customers whose grade are higher than customers living in New York City. Return customer_id, cust_name, city, grade and salesman_id.
27. From the following tables, write a SQL query to calculate the total order amount generated by a salesman. The salesman should belong to the cities where any of the customer living. Return salesman name, city and total order amount.
28. From the following tables, write a SQL query to find those customers whose grade doesn't same of those customers live in London City. Return customer_id, cust_name, city, grade and salesman_id.
29. From the following tables, write a SQL query to find those customers whose grade are not same of those customers living in Paris. Return customer_id, cust_name, city, grade and salesman_id.
30. From the following tables, write a SQL query to find all those customers who have different grade than any customer lives in Dallas City. Return customer_id, cust_name,city, grade and salesman_id.
31. From the following tables, write a SQL query to find the average price of each manufacturer's product along with their name. Return Average Price and Company.
32. From the following tables, write a SQL query to calculate the average price of the products and find price which are more than or equal to 350. Return Average Price and Company.
33. From the following tables, write a SQL query to find the most expensive product of each company. Return Product Name, Price and Company.
34. From the following tables, write a SQL query to find those employees whose last name is 'Gabriel' or 'Dosio'. Return emp_idno, emp_fname, emp_lname and emp_dept.
35. From the following tables, write a SQL query to find the employees who work in department 89 or 63. Return emp_idno, emp_fname, emp_lname and emp_dept.
36. From the following tables, write a SQL query to find those employees who work for the department where the department allotment amount is more than Rs. 50000. Return emp_fname and emp_lname.
37. From the following tables, write a SQL query to find the departments where the sanction amount is higher than the average sanction amount of all the departments. Return dpt_code, dpt_name and dpt_allotment.
38. From the following tables, write a SQL query to find the departments where more than two employees work. Return dpt_name.
39. From the following tables, write a SQL query to find the departments where the sanction amount is second lowest. Return emp_fname and emp_lname.