# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql  
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email


PROGRAN :
```sql
insert into Customers(CustomerID, Name, Address, Email)
select * from Old_customers;
```

**Output:**

<img width="1281" height="366" alt="image" src="https://github.com/user-attachments/assets/11448a5a-e6ad-4381-ac5f-e74166f055c5" />


**Question 2**
---
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

PROGRAN :
```sql
create table Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE
);
```

**Output:**

<img width="1255" height="433" alt="image" src="https://github.com/user-attachments/assets/be06e8da-5195-4158-8b6f-b655499fa605" />

**Question 3**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.

PROGRAN :
```sql
create table Attendance(
AttendanceID INTEGER primary key,
EmployeeID INTEGER, 
AttendanceDate DATE,
Status TEXT check(status in ('Present','Absent','Leave')),
foreign key (EmployeeID)references Employees(EmployeeID)
);

```

**Output:**

<img width="1325" height="380" alt="image" src="https://github.com/user-attachments/assets/ede8da68-7f2c-4e9c-9ab0-2ada280979c2" />

**Question 4**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
designation as VARCHAR(50)
net_salary as NUMBER
dob as DATE


PROGRAN :
```sql
alter table Companies add column designation varchar(50);
alter table Companies add column net_salary number; 
alter table Companies add column dob date;
```

**Output:**

<img width="1303" height="470" alt="image" src="https://github.com/user-attachments/assets/9409d501-cc24-4c98-99f0-4b86c0d18133" />

**Question 5**
---
Write a SQL Query for inserting the below values in the table Customers

ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000


PROGRAN :
```sql
insert into Customers(ID,NAME,AGE ,ADDRESS,SALARY ) values('1','Ramesh','32','Ahmedabad','2000'),('2','Khilan','25','Delhi','1500'),('3','Kaushik','23','Kota','2000');
```

**Output:**

<img width="1303" height="360" alt="image" src="https://github.com/user-attachments/assets/f2865fd7-95b5-4e9c-875c-314c93e81d49" />

**Question 6**
---
Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.



PROGRAN :
```sql
alter table Student_details add column MobileNumber NUMBER;
alter table Student_details add column Address VARCHAR(100);
 ```

**Output:**

<img width="1292" height="439" alt="image" src="https://github.com/user-attachments/assets/212a393a-3a6c-4a6b-87e9-f9320db8ea4d" />

**Question 7**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.


PROGRAN :
```sql
create table item(
item_id  TEXT primary key,
item_desc TEXT not null,
rate  INTEGER not null,
icom_id  TEXT icom_id(4), 
foreign key (icom_id)
    references company(com_id)
    on update cascade
    on delete cascade
);
```

**Output:**

<img width="1273" height="430" alt="image" src="https://github.com/user-attachments/assets/4d9bca8d-4bec-48cc-9c6b-39f07af5afad" />

**Question 8**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.


PROGRAN :
```sql
insert into Books(ISBN,Title,Author,Publisher,Year) values('978-1234567890','Data Science Essentials','Jane Doe','TechBooks','2024');
```

**Output:**

<img width="1266" height="308" alt="image" src="https://github.com/user-attachments/assets/7caca4b1-a46d-4cf8-916e-df133dd488b9" />

**Question 9**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

PROGRAN :
```sql
create table Bonuses(
BonusID INTEGER primary key,
EmployeeID INTEGER ,
BonusAmount  REAL check(BonusAmount>0),
BonusDate DATE,
Reason TEXT  not NULL,
foreign key (EmployeeID)references Employees(EmployeeID)
);
```

**Output:**

<img width="1283" height="352" alt="image" src="https://github.com/user-attachments/assets/af306399-0153-438c-a767-bd03b42ef07d" />

**Question 10**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.


PROGRAN :
```sql
Create table ProjectAssignments(
AssignmentID  INTEGER primary key,
EmployeeID INTEGER ,
ProjectID INTEGER ,
AssignmentDate  DATE NOT NULL, 
foreign key (EmployeeID)references Employees(EmployeeID),
foreign key (ProjectID) references Projects(ProjectID)
);
```

**Output:**

<img width="1279" height="370" alt="image" src="https://github.com/user-attachments/assets/0b2a1a5d-5c02-4781-b3c1-7b2730a4cdb8" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
