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
How many doctors specialize in each medical specialty?

```sql
select Specialty,count(*) as TotalDocto
from Doctors
group by Specialty;
```

**Output:**

<img width="479" alt="image" src="https://github.com/user-attachments/assets/65e3403d-a48a-4bed-a892-65a93cb451dd" />


**Question 2**
---
How many appointments are scheduled for each patient?

```sql
select PatientID,count(*) as TotalAppointments
from Appointments
group by PatientID;
```

**Output:**

<img width="490" alt="image" src="https://github.com/user-attachments/assets/cc255bc2-b07f-44c8-87e1-c47663bba129" />


**Question 3**
---
What is the most common diagnosis among patients?

```sql
select Diagnosis,count(*) as DiagnosisCount
from MedicalRecords
group by Diagnosis
order by DiagnosisCount desc
limit 1;
```

**Output:**

<img width="551" alt="image" src="https://github.com/user-attachments/assets/7f4bd00c-98a2-41d7-94af-1df5ff768d74" />


**Question 4**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

```sql
select count(grade) as COUNT
from customer
where grade is not null;
```

**Output:**

<img width="341" alt="image" src="https://github.com/user-attachments/assets/8e665fb2-d495-489f-9f27-be76b45b1da9" />


**Question 5**
---
Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL

```sql
select sum(Inventory) as total_available_amount
from fruits
where price>0.5;
```

**Output:**

<img width="587" alt="image" src="https://github.com/user-attachments/assets/7e77616a-cbde-4469-b34b-ea14d3cc0544" />


**Question 6**
---
Write a SQL query to  find the average salary of all employees?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
select avg(income) as Average_Salary
from employee;
```

**Output:**

<img width="556" alt="image" src="https://github.com/user-attachments/assets/06a3c271-d52e-47b2-a22f-3e864add0a8b" />


**Question 7**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL

```sql
select sum(Inventory) as total
from fruits
where unit like ('LB');
```

**Output:**

<img width="511" alt="image" src="https://github.com/user-attachments/assets/dff0dc24-fad4-4849-a98a-8140de4a13a5" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

```sql
select jdate,MIN(workhour) 
from employee1
group by jdate
having MIN(workhour)<10;
```

**Output:**

<img width="601" alt="image" src="https://github.com/user-attachments/assets/ee4a3f21-a082-46d5-9601-1b7e2efffda4" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.

```sql
select age,MAX(income) 
from employee
group by age
having MAX(income)>2000000;
```

**Output:**

<img width="556" alt="image" src="https://github.com/user-attachments/assets/abf2d4ba-13ea-4ef5-adbb-cef98ff0c937" />


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

```sql
select age,AVG(income)
from employee
group by age
having AVG(income) between 300000 and 500000;
```

**Output:**

<img width="560" alt="image" src="https://github.com/user-attachments/assets/54787944-8c2f-443e-b9cd-402ba4cb993e" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
