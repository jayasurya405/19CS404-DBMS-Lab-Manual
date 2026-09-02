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
<img width="1033" height="251" alt="Screenshot 2026-08-28 114415" src="https://github.com/user-attachments/assets/ad3d577d-e8bf-4118-8f2a-e374142e0180" />


```sql
select Address ,count(*) as TotalPatients from Patients group by Address;
```

**Output:**
<img width="757" height="427" alt="Screenshot 2026-08-28 114444" src="https://github.com/user-attachments/assets/43319404-5078-4d9a-93ed-24d4359ed8b8" />

**Question 2**
---
<img width="1007" height="225" alt="Screenshot 2026-08-28 114505" src="https://github.com/user-attachments/assets/d611dbee-86f0-4ed0-b712-c6366c746e91" />


```sql
select PatientID, count(*)  as TotalMedications from Prescriptions group by PatientID;
```

**Output:**

<img width="712" height="762" alt="Screenshot 2026-08-28 114541" src="https://github.com/user-attachments/assets/98ba8d66-960f-4291-8c7f-7c7d138088df" />

**Question 3**
```---
What is the average duration of insurance coverage for patients covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
StartDate          DATE
EndDate            DATE
```

```sql
select InsuranceCompany,avg(EndDate-StartDate) as AvgCoverageDurationDays from Insurance group by InsuranceCompany;
```

**Output:**

<img width="897" height="672" alt="Screenshot 2026-08-28 114632" src="https://github.com/user-attachments/assets/4ef8ae24-4f4e-42b3-bc5a-bfef9e99b688" />


**Question 4**
```---
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
```
```sql
select count(distinct city) as unique_cities from customer;
```

**Output:**
<img width="480" height="297" alt="Screenshot 2026-08-28 114714" src="https://github.com/user-attachments/assets/bdca9418-4f82-4abb-9edd-4a150d547312" />


**Question 5**
---
<img width="946" height="282" alt="Screenshot 2026-08-28 114733" src="https://github.com/user-attachments/assets/ef00836d-7b21-402c-b155-5a91892b0795" />


```sql
select count(*) as COUNT from customer where city!='Noida';
```

**Output:**
<img width="380" height="307" alt="Screenshot 2026-08-28 114811" src="https://github.com/user-attachments/assets/18ae9ab7-a24b-4711-901a-83cb28ad56ff" />


**Question 6**
```---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```
```sql
select avg(income) as avg_income from employee where name like 'A%';
```

**Output:**
<img width="407" height="312" alt="Screenshot 2026-08-28 114909" src="https://github.com/user-attachments/assets/4ba864a5-e285-4f79-a40f-78587dea569c" />


**Question 7**
```---
Write a SQL query to find  how many employees work in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 
```
```sql
select count(*) as employees_in_california from employee where city='California';
```

**Output:**
<img width="640" height="317" alt="Screenshot 2026-08-28 115032" src="https://github.com/user-attachments/assets/06e57e22-0332-408f-969f-0c12d65d8bbf" />


**Question 8**
---
<img width="1162" height="260" alt="Screenshot 2026-08-28 115059" src="https://github.com/user-attachments/assets/8ffa101c-4768-4a57-b1aa-ccfe15d350a7" />


```sql
select (age/5)*5 as age_group, min(salary) as "MIN(salary)" from customer1 group by (age/5)*5 having min(salary)<2000;
```

**Output:**

<img width="613" height="321" alt="Screenshot 2026-08-28 115140" src="https://github.com/user-attachments/assets/855a16d5-05b4-4153-a6f9-70be030a96ea" />


**Question 9**
---
<img width="1188" height="275" alt="Screenshot 2026-08-28 115210" src="https://github.com/user-attachments/assets/026c682c-3381-4363-be70-b3c5fb4be471" />


```sql
select category_id, sum(price) as Total_Cost from products group by category_id having Total_Cost>50;
```

**Output:**
<img width="600" height="341" alt="Screenshot 2026-08-28 115241" src="https://github.com/user-attachments/assets/963f6242-9faf-47fd-a230-296def0c080e" />


**Question 10**
---
<img width="1221" height="261" alt="Screenshot 2026-08-28 115322" src="https://github.com/user-attachments/assets/d5c43c9c-6f05-43f1-97df-f4d8745e9a87" />


```sql
select jdate,max(workhour) as "MAX(workhour)" from employee1 group by jdate having max(workhour)>12;
```

**Output:**
<img width="652" height="377" alt="Screenshot 2026-08-28 115401" src="https://github.com/user-attachments/assets/f3bcf3eb-e945-4445-bd40-a61bc73b0b1e" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
