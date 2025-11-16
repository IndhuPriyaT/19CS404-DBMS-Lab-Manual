# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
-- Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column.

```sql
-- select s.name , c.cust_name , c.city , c.grade , c.salesman_id from Salesman s left join Customer c on
s.salesman_id = c.salesman_id;
```

**Output:**

<img width="1237" height="921" alt="image" src="https://github.com/user-attachments/assets/6424b4dc-ed9f-4b4d-be50-4682953cac4a" />


**Question 2**
---
-- Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.

```sql
-- select s.name from Salesman s left join Customer c on s.salesman_id = c.salesman_id where c.city = 'London';
```

**Output:**

<img width="555" height="570" alt="image" src="https://github.com/user-attachments/assets/356b183e-29f0-452a-ae92-0cc6db9d7df7" />

**Question 3**
---
-- PFrom the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12

```sql
--select c.cust_name as "Customer Name" , c.city , s.name as "Salesman" , s.city , s.commission from customer c 
inner join salesman s on c.salesman_id = s.salesman_id where s.city != c.city and s.commission > 0.12; 
```

**Output:**

<img width="1236" height="701" alt="image" src="https://github.com/user-attachments/assets/6c835e20-4d73-4370-a7e2-bef7e012a5cc" />


**Question 4**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

```sql
-- select p.first_name as "patient_name" , t.test_name from test_results t inner join patients p on t.patient_id 
= p.patient_id;
```

**Output:**

<img width="877" height="637" alt="image" src="https://github.com/user-attachments/assets/73766a2d-00fa-4d33-bac1-38950b6609a9" />


**Question 5**
---
-- Write the SQL query that accomplishes the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:

name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

SURGERIES TABLE:

name             type
---------------  ---------------
surgery_id       INT
patient_id       INT
surgeon_id       INT
surgery_date     DATE
```sql
-- select p.first_name , s.* from surgeries s  inner join patients p on s.patient_id = p.patient_id 
where p.first_name = 'Alice';
```

**Output:**

<img width="1229" height="508" alt="image" src="https://github.com/user-attachments/assets/8c4c62d9-1297-4817-b362-c2099264cffd" />


**Question 6**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

```sql
-- select p.first_name as "patient_name" ,t.* from test_results t inner join patients p on t.patient_id = p.patient_id;
```

**Output:**

<img width="1227" height="647" alt="image" src="https://github.com/user-attachments/assets/68c7f3d6-d364-41a3-b9de-b29b41fe3e4f" />


**Question 7**
---
-- Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c") and the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the same city as the salesman.

```sql
-- select c.cust_name , s.name from salesman s left join customer c on s.salesman_id = c.salesman_id where 
c.city = s.city;
```

**Output:**

<img width="867" height="641" alt="image" src="https://github.com/user-attachments/assets/df1e7c99-f7f0-45de-8a54-bc66bba45b0a" />


**Question 8**
---
-- From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001

```sql
-- select o.ord_no , o.purch_amt , c.cust_name , c.city from customer c inner join
orders o on c.customer_id = o.customer_id where o.purch_amt between 500 and 2000;
```

**Output:**

<img width="1234" height="584" alt="image" src="https://github.com/user-attachments/assets/7ea0f1b9-b8e2-4ece-bb65-ee4517b4aa47" />


**Question 9**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a null discharge date.

```sql
-- select p.first_name as "patient_name", d.first_name as "doctor_name" from doctors d inner join
patients p on d.doctor_id = p.doctor_id where discharge_date IS NULL;
```

**Output:**

<img width="815" height="558" alt="image" src="https://github.com/user-attachments/assets/306c0d4d-d571-4107-957f-48951c42c0b9" />


**Question 10**
---
-- Write the SQL query that achieves the selection of the date of birth from the "patients" table (aliased as "p") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'

```sql
-- select p.date_of_birth , a.* from appointments a inner join patients p on a.patient_id = p.patient_id where 
p.first_name = 'Alice';
```

**Output:**

<img width="1230" height="498" alt="image" src="https://github.com/user-attachments/assets/c880d920-d267-4c44-b973-1d3a6f8828b2" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
