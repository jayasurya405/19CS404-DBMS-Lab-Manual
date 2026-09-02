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
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id


PROGRAM :
```sql
update products
set reorder_lvl=20 where quantity<10 and category ='Snacks';
```

**Output:**

<img width="1297" height="643" alt="image" src="https://github.com/user-attachments/assets/8f1d6ff9-465c-49dd-93f7-e0843f84a6da" />

**Question 2**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

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

PROGRAM :
```sql
update employees
set email='not available',commission_pct='0.55' where department_id =110;
```

**Output:**

<img width="1281" height="433" alt="image" src="https://github.com/user-attachments/assets/c3f2fc7c-3259-4316-aa3c-059c535e6dcc" />

**Question 3**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

PROGRAM :
```sql
update products
set product_name='Grapefruit' where product_id=4;
```

**Output:**

<img width="1293" height="258" alt="image" src="https://github.com/user-attachments/assets/0d31b097-3d89-49d5-ad6a-f0fa6364c894" />

**Question 4**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

PROGRAM :
```sql
update suppliers
set supplier_name=UPPER(supplier_name) where contact_person like '%Singh%';
```

**Output:**

<img width="1304" height="441" alt="image" src="https://github.com/user-attachments/assets/f0b4f042-f848-4a56-ae4a-fcc9d74ba96d" />

**Question 5**
---
Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules.

Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.

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

PROGRAM :
```sql
update employees
set salary=salary+(salary*25/100) 
where department_id=40; 
update employees
set salary=salary+(salary*15/100) 
where department_id=90; 
update employees
set salary=salary+(salary*10/100)  
where department_id=110;
```

**Output:**

<img width="1265" height="512" alt="image" src="https://github.com/user-attachments/assets/d7293fdf-c7db-4e1e-b72c-68416f8060ff" />

**Question 6**
---
Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

PROGRAM :
```sql
delete from doctors
where doctor_id between 2 and 4;
```

**Output:**

<img width="1250" height="776" alt="image" src="https://github.com/user-attachments/assets/71f0166f-974c-4723-8927-58602f607deb" />

**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

PROGRAM :
```sql
delete from customer
where grade =2;
```

**Output:**

<img width="714" height="522" alt="image" src="https://github.com/user-attachments/assets/778c4d57-3088-438b-9afd-fb48a0a8b739" />

**Question 8**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

PROGRAM :
```sql
delete from doctors
where specialization = 'Pediatrics' 
and first_name='Michael';
```

**Output:**

<img width="1307" height="405" alt="image" src="https://github.com/user-attachments/assets/b01e5263-cd1c-4486-9a60-aaad3dd89fc7" />

**Question 9**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

PROGRAM :
```sql
delete from surgeries
where surgery_id=3;
```

**Output:**

<img width="1284" height="425" alt="image" src="https://github.com/user-attachments/assets/17a11bc6-2242-481b-b993-cff85598bc19" />

**Question 10**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |


PROGRAM :
```sql
delete from customer
where (grade>2 and payment_amt<(select avg(payment_amt) from customer))
or outstanding_amt>8000;
```

**Output:**

<img width="1300" height="720" alt="image" src="https://github.com/user-attachments/assets/31fe97c9-47a6-49d5-8c30-c257bacbc60a" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
