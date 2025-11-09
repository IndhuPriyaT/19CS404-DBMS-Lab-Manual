# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
--Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.

```sql
-- delete from customer where AGENT_CODE = 'A003' or AGENT_CODE = 'A008';
```

**Output:**

<img width="791" height="880" alt="image" src="https://github.com/user-attachments/assets/d3fafcae-fc54-43de-930c-f04cc135ac85" />


**Question 2**
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

```sql
-- delete from Customer where "CUST_NAME" like '%Holmes%';
```

**Output:**

<img width="1231" height="631" alt="image" src="https://github.com/user-attachments/assets/b18a4bcd-7945-45c8-8187-8613d20f8d87" />


**Question 3**
---
--Write a SQL query to classify base in the Calculations table as 'Provided' if it is not NULL, otherwise 'Not Provided'.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```sql
--select id , base , case
when base is NOT NULL then "Provided"
when base is NULL then "Not Provided"
end as base_status from Calculations;
```

**Output:**

<img width="1227" height="567" alt="image" src="https://github.com/user-attachments/assets/7031e46a-edf2-4342-905a-c7edf8d97e3d" />


**Question 4**
---
--Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

```sql
--delete from Customer where cust_city like "L%";
```

**Output:**

<img width="1238" height="331" alt="image" src="https://github.com/user-attachments/assets/04f425e9-c771-4adf-837f-0bc1d88e08a5" />


**Question 5**
---
-- Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'


Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id 
```sql
--update Employees set salary = salary * 2 where department_id = 20 and job_id like "%MAN"
```

**Output:**

<img width="1228" height="435" alt="image" src="https://github.com/user-attachments/assets/0564786b-21ce-4ece-99ce-358eb7e52be1" />


**Question 6**
---
-- Paste Question 6 hereWrite a SQL query to calculate the discounted price for each product. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage
------------+----------------+---------------------
101 | 50.00 | 0.10
102 | 75.00 | 0.15
103 | 100.00 | 0.20

```sql
-- select product_id , original_price , discount_percentage , original_price*(1-discount_percentage) as discounted_price from Products;
```

**Output:**

<img width="1239" height="536" alt="image" src="https://github.com/user-attachments/assets/e865a959-6115-452b-a9e2-da6551b6286e" />


**Question 7**
---
--Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

```sql
-- delete from Customer where GRADE = 3 and  CUST_NAME like "%BBB%" and PAYMENT_AMT > 2000;
```

**Output:**

![Output7](output.png)<img width="1235" height="595" alt="image" src="https://github.com/user-attachments/assets/634f7af4-0776-49db-b5e2-e6530ac33a4c" />


**Question 8**
---
-- write a SQL query to find details of all orders with a purchase amount less than 200 or exclude orders with an order date greater than or equal to '2012-02-10' and a customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.



```sql
-- select * from orders where purch_amt < 200 or not (ord_date >= '2012-02-10' and customer_id < 3009);
```

**Output:**

<img width="1241" height="565" alt="image" src="https://github.com/user-attachments/assets/03248069-930f-4b60-9629-bb2eedd84cb5" />


**Question 9**
---
-- Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15


Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id 

```sql
-- update Employees set salary = salary + 500 , email = 'updated' where job_id = 'SA_REP' and commission_pct > 0.15;
```

**Output:**

<img width="1242" height="605" alt="image" src="https://github.com/user-attachments/assets/cfc0c90a-2a92-4eee-90cf-e6cdc346ebef" />



**Question 10**
---
--Write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id.

```sql
--select * from customer where grade is NULL;
```

**Output:**

<img width="1235" height="518" alt="image" src="https://github.com/user-attachments/assets/c32b61b1-a99d-4ccc-97d1-cc5166cf2907" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
