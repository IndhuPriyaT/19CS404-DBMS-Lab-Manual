# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
-- Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

 

```sql
-- select count(grade) as COUNT from customer;
```

**Output:**

<img width="675" height="398" alt="image" src="https://github.com/user-attachments/assets/ba225b61-e93d-45a0-9171-18c0ad0e8918" />


**Question 2**
---
-- Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
-- select max(purch_amt) as MAXIMUM from orders;
```

**Output:**

<img width="461" height="394" alt="image" src="https://github.com/user-attachments/assets/e611ef04-7f29-4615-9955-db4e3a8ecc02" />


**Question 3**
---
-- Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
-- select sum(purch_amt) as TOTAL from orders;
```

**Output:**

<img width="452" height="401" alt="image" src="https://github.com/user-attachments/assets/d6c5dba4-6641-4173-bf5b-f2b9fc4dce24" />


**Question 4**
---
--Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

```sql
--select PatientId , count(Medications) as AvgMedications from MedicalRecords group by PatientId;
```

**Output:**

<img width="742" height="636" alt="image" src="https://github.com/user-attachments/assets/d307e878-4872-4e75-816d-42c6c535a17f" />

**Question 5**
---
-- What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table

```sql
-- select PatientId , count(Medication) as TotalMedications from Prescriptions group by PatientId;
```

**Output:**

<img width="766" height="838" alt="image" src="https://github.com/user-attachments/assets/93e671be-bcef-4ca6-822e-75e4ae2ddd93" />


**Question 6**
---
-- How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table

```sql
-- select Specialty , Gender , count(Gender) as TotalDoctors from Doctors group by Specialty,Gender;
```

**Output:**

<img width="952" height="742" alt="image" src="https://github.com/user-attachments/assets/d4084271-8154-4bd6-9bf1-187e4b2f6da4" />


**Question 7**
---
-- Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee
```sql
-- select age, min(income) as Income from employee where Income < 1000000 group by age;
```

**Output:**

<img width="729" height="520" alt="image" src="https://github.com/user-attachments/assets/b49d988f-5dba-439f-9811-91f79cd07e7f" />


**Question 8**
---
-- Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

Sample table: employee

```sql
-- select age, AVG(income) as "AVG(income)"  from employee group by age having AVG(income) between 300000 and 500000; 
```

**Output:**

<img width="743" height="441" alt="image" src="https://github.com/user-attachments/assets/5d42cc0f-f2e4-4a53-86e4-e68a65eaa32b" />


**Question 9**
---
-- Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

Sample table: customer1

```sql
-- select address , AVG(salary) as "AVG(salary)" from customer1 group by address having AVG(salary) < 15000;
```

**Output:**

<img width="770" height="694" alt="image" src="https://github.com/user-attachments/assets/f9de0f59-5ae0-45be-add4-2ddac53a4658" />


**Question 10**
---
-- Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

Sample table: employee
```sql
-- select age , SUM(income) as "SUM(income)" from employee group by age having SUM(income) > 1000000;
```

**Output:**

<img width="701" height="502" alt="image" src="https://github.com/user-attachments/assets/acfe54e7-2496-4726-aad8-7b308de6644c" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
