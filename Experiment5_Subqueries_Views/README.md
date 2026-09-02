# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
```--
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```
```sql
select * from customers where ADDRESS='Delhi' and AGE<30 order by ID asc;
```

**Output:**
<img width="1220" height="357" alt="Screenshot 2026-08-28 100524" src="https://github.com/user-attachments/assets/547c590a-698b-4120-9868-cd2e7ba10abd" />


**Question 2**
```---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000


```

```sql
select * from CUSTOMERS where salary<2500;
```

**Output:**
<img width="1227" height="455" alt="Screenshot 2026-08-28 100643" src="https://github.com/user-attachments/assets/d4b83e31-5a7e-4646-b544-d432699252e3" />


**Question 3**
```---
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)
```
```sql
select * from Medications where dosage=(select max(dosage) from Medications);
```

**Output:**
<img width="932" height="391" alt="Screenshot 2026-08-28 100755" src="https://github.com/user-attachments/assets/faa873ff-964e-460b-8949-010b1587aec2" />


**Question 4**
```---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)
```
<img width="742" height="300" alt="Screenshot 2026-08-28 100839" src="https://github.com/user-attachments/assets/05e56649-619b-4ea0-ac46-0ce5482e1729" />

```sql
-SELECT student_name, grade
FROM GRADES
WHERE (subject, grade) IN (
    SELECT subject, MAX(grade)
    FROM GRADES
    GROUP BY subject
);
```

**Output:**
<img width="767" height="417" alt="Screenshot 2026-08-28 100937" src="https://github.com/user-attachments/assets/69652466-05c2-448c-a16b-106ccd6639aa" />


**Question 5**
```---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

customer table

name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int
```

```sql
select * from customer where customer_id=(select salesman_id-2001 from salesman where name='Mc Lyon');
```

**Output:**
<img width="1245" height="297" alt="Screenshot 2026-08-28 101038" src="https://github.com/user-attachments/assets/307fe9e6-3e08-47d4-a2b4-d00cf6383ef3" />


**Question 6**
```---
From the following tables write a SQL query to find all orders generated by New York-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```
```sql
select * from orders where salesman_id in(select salesman_id from salesman where city='New York');
```

**Output:**
<img width="1253" height="468" alt="Screenshot 2026-08-28 110733" src="https://github.com/user-attachments/assets/5f2117a5-5608-47e8-a680-933e7a8a77ec" />



**Question 7**
```---
Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

SAMPLE TABLE: customer

name             type
---------------  ---------------
id               INTEGER
name             TEXT
city             TEXT
email            TEXT
phone            INTEGER
```
```sql
select * from customer where city !=(select city from customer order by id desc limit 1);
```

**Output:**
<img width="1252" height="496" alt="Screenshot 2026-08-28 111145" src="https://github.com/user-attachments/assets/258b9071-c868-489d-9e5c-8abbe11fcfce" />


**Question 8**
```---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```
```sql
select * from customers where ADDRESS='Delhi';
```

**Output:**
<img width="1228" height="342" alt="Screenshot 2026-08-28 113253" src="https://github.com/user-attachments/assets/3ec0406d-4f53-46fe-b053-c55251ef5409" />


**Question 9**
```---
From the following tables write a SQL query to find all orders generated by London-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
 
```
```sql
select * from orders where salesman_id in (select salesman_id from salesman where city='London');
```

**Output:**
<img width="1297" height="416" alt="Screenshot 2026-08-28 113455" src="https://github.com/user-attachments/assets/486c12af-bf58-4555-8940-f0b13ddec23a" />


**Question 10**
```---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

salesman table

name                 type
---------------   ---------------
salesman_id       numeric(5)
name                  varchar(30)
city                     varchar(15)
commission       decimal(5,2)

customer table

name              type
-----------       ----------
customer_id   int
cust_name     text
city                text
grade            int
salesman_id  int
```
```sql
select s.salesman_id,s.name from salesman as s join customer as c on s.salesman_id=c.salesman_id group by s.salesman_id,s.name having count(customer_id)>1;
```

**Output:**
<img width="642" height="462" alt="Screenshot 2026-08-28 113602" src="https://github.com/user-attachments/assets/9b447a29-128a-4bea-9f5d-072c94f80f38" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
