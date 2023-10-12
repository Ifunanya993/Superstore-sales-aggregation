# INTRODUCTION

## DATA AGGREGATION

Data summarization using SQL involves aggregating and summarising data from a database to obtain
meaningful insights or condense large datasets into more managable and understandable forms.

AGGREGATE functions in SQL are used to perform calculations on sets of values and returns a single result.
These functions are often applied to columns in a database table to summarize data. Commonly used aggregate 
functions in SQL:

### SUM:
Calculates the sum of numeric values in a column

syntax : SLECT SUM(sales) FROM Superstore;

### COUNT:
Counts the number of rows in a result set.

synyax: COUNT(*) FROM Superstore;

### AVG:
Computes the average of numeric values in a column.

Syntax : SELECT AVG(sales) FROM superstore;

### MIN:
Returns the minimum value from a column

Syntax : SELECT MIN(sales)  FROM superstore;

### MAX:
Retrieves the maximum value from a column.

Syntax : SELECT MAX(sales)  FROM superstore;

------------------------

## DATA SUMMARIZATION WITH SQL'S GROUP BY, HAVING CLAUSE, ORDER BY AND LIMIT

### GROUP BY:
This allows you to group rows that have the same values specified in columns. You can then use aggregate functions
to summarise data within each group.

syntax : SELECT product, avg(profit) AS avg_profit FROM superstore GROUP BY product;

### HAVING CLAUSE :
This is used in combination with GROUP BY to filter groups based on aggregate values. it helps you apply conditions
to aggregate data.

Syntax : SELECT city, sum(sales) as sales  FROM superstore GROUP BY city  HAVING sale > 2000;

### ORDER BY :
This is used when grading your aggregated value in ASCENDING (ASC) or DESCENDING (DESC) order.

Syntax : SELECT customer_name, sum(profit) AS profit FROM superstore GROUP BY Customer_name ORDER BY Profit DESC;

### LIMIT :
This works in combination of ORDER BY to reduce or shorten your result.

Syntax : SELECT Customer_name, sum(profit) AS profit FROM superstore GROUP BY customer_name ORDER BY profit DESC LIMIT 

---------------------------

## DATA SUMMARIZATION USING JOINS AND SUBQUERIES

JOINS are essential for combining data from multiple tables in a relational database. They allow you to retrieve meaningful 
information by establishing relationships between tables . There are different types of JOINS

### INNER JOIN :
This retrieves rows that have maching values in both tables

Syntax : SELECT column

FROM table1

INNER JOIN  table2 ON  table1.column = table2.column;

 ### LEFT JOIN :
This retrieves all rows from the left table and matching rows from the right table

Syntax : SELECT column

FROM table1

LEFT JOIN table2 ON table1.colum = table2.column;

### RIGHT JOIN :
Retrieves all rows from the right table and matching rows from the left table

Syntax : SELECT column

FROM table1

RIGHT JOIN table2 ON table1.column = table2.column;

### FULL OUTER JOIN :
Retrieves all rows when there is a match in either the left or right table.

Syntax : SELECT column

FROM table1

FULL OUTER JOIN table2 ON table1.column = table2.column;

-----------------


## COMMON TABLE EXPRESSION (CTEs) 
Common Table Expression (CTEs) are a powerful and useful feature in SQL, for creating temporary result sets that 
can be referenced within a SELECT, INSERT, UPDATE, or DELETE statement.
It makes complex queries more readable and maintainable by breaking them into smaller logical parts.

Syntax:

WITH cte_name(column1, column2,...) AS (    )

SELECT  * FROM cte name;


## ROW NUMBER() 
This assigns a unique integer to each row within the result sets, starting from 1 for the first row and incrementing by 1
for each subsquent row. Rows with equal values will get distinct numbers.

Syntax :

SELECT column1, column2

ROW NUMBER() OVER (ORDER BY column DESC/ASC) AS Number

FROM table name;







## PROBLEM SOLVING
Using already existed Superstore Dataset solve the following

- How many rows are in the SALES table provided?
- The business is operating in how many Regions ?
- What is the Total Profit generated in the WEST Region?
- What is the Average Profit generated from Sales of the company's products ?
- How many Products does the company sells?
- Show the Names and cities of the 5 customers who contributed most to the overall Profit ?
- Show the Sales generated by Cities where the Total Sales is greater than 2000?

Using already existed Employee, Salary and Department Datasets, to solve the following 4
business questions that comprises: JOIN, GROUP BY, AT LEAST 2 AGGREGATES FUNCTIONS AND ORDER.
The Business questions includes:

- What is the average yearly increment of Salary?
- Run a query that shows name and yearly increment of salary using JOIN command.
- What is the Employee ID with the minimum yearly increment?
- Run a query that shows employee name and designation 

## ANSWER

To import a Dataset

- CREATE A DATABASE 
- Right click on the Database created
- Click on IMPORT TABLE WIZARD
- Browse the file you saved it with and tick drop table if alreadt existed in the Database, click next
- Format the Data type appropraiately, click next
- Your table will import , click finish 
- Refresh Schema , click on the Database. your table is ready 

- ### How many rows are in the SALES table
  The Database is named SALES
  The Table name is Superstore
  
#### SYNTAX
USE Sales;

SELECT COUNT(Sales) FROM Superstore;

- ### How many Regions does the Business operates in

#### SYNTAX
USE Sales;

SELECT COUNT(DISTINCT Region) FROM Superstore;

- ### Total Profit generated in the WEST Region

#### SYNTAX
USE Sales;

SELECT Region, sum(Sales) AS Total Profit 

FROM Superstore

WHERE Region = "WEST";

- ### The Average Profit generated from the SALES of Company's Products

#### SYNTAX
USE Sales;

SELECT Products name, Avg(profit) as Sales

FROM Superstore

GROUP BY Product name;

- ### Count of Products sold

#### Syntax
USE Sales;

SELECT Count(distinct prdouct name)

FROM Superstore;


- ### Run a query to show 5 customer names and city that contributes most in profit

#### Syntax
USE Sales;

SELECT Customer name , round(sum(profit), 0) AS Profit

FROM Superstore

GROUP BY Customer name

ORDER BY Profit DESC

LIMIT 5;

#### FOR CITY

USE Sales;

SELECT City , round(sum(profit), 0) AS Profit

FROM Superstore

GROUP BY  City

ORDER BY Profit DESC

LIMIT 5;


- ### Cities where Total Sales is greater than 2000

#### Syntax
USE SALES;

SELECT City, round (sum(Sales), 0) AS Sales

FROM superstore

GROUP BY City

HAVING Sale > 2000;


## 4 Business questions that comprises JOIN, GROUP BY, AGGREGATE FUNCTION AND ORDER
The name of the Database is COMPANY

- ### Average yearly increment of the Salary

Syntax : USE Company;

SELECT avg(`yearly increment`) FROM Salary;

- ### To a query that shows employee name and yearly increment usig JOIN

Syntax : USE Company;

SELECT name, fname, `yearly increment`  

FROM EMPLOYEE

JOIN SALARY

ON Employee.EmpID = Salary.EmpID;

- ### Employee ID with the minimum `yearly increment`

Syntax : USE Company;

SELECT Emp ID, MIN( `Yearly increment) AS `Yearly increment`

FROM Salary

GROUP BY EmpID

ORDER BY `Yearly increment ASC;

- ### Run a query that shows full name and designation

Syntax : USE Company

SELECT name, fname, designation

FROM Employee

JOIN Department

ON Employee.DeptID = Department.DeptID;














