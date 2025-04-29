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
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct is less than .35.

```sql
update  EMPLOYEES
set first_name = "John"
where department_id = 80; 
```

**Output:**

<img width="935" alt="image" src="https://github.com/user-attachments/assets/270cdc26-dd39-4e3f-b793-e85dea9682f9" />


**Question 2**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

```sql
update suppliers
set supplier_name =upper(supplier_name)
where contact_person like "%Singh%";
```

**Output:**

<img width="908" alt="image" src="https://github.com/user-attachments/assets/8cbf0db3-3442-446f-897e-c82a054fedcd" />


**Question 3**
---
Write a SQL statement to double the availability of the product with product_id 1.

```sql
update PRODUCTS
set availability = availability*2
where product_id  = 1;
```

**Output:**

<img width="658" alt="image" src="https://github.com/user-attachments/assets/cb6f4107-a89f-42d6-9376-b9e526ef0b8e" />


**Question 4**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

                              

```sql
update   EMPLOYEES
set EMAIL = "not available", 
 COMMISSION_PCT = 0.55
where DEPARTMENT_ID = 110;
```

**Output:**

<img width="821" alt="image" src="https://github.com/user-attachments/assets/4c3e9a73-bfaa-4b69-9e37-3480d0eb7367" />


**Question 5**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

```sql
delete  from Doctors
where last_name IS NULL;
```

**Output:**

<img width="662" alt="image" src="https://github.com/user-attachments/assets/3353b625-8800-4728-a1d8-73da57b73497" />


**Question 6**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

```sql
delete from Customer
where cust_city LIKE"L%";
```

**Output:**

<img width="926" alt="image" src="https://github.com/user-attachments/assets/4fb910d8-0951-4b75-bb93-cb2a00554be7" />


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

```sql
delete from Customer
where CUST_CITY != 'New York' 
and OUTSTANDING_AMT > 5000;
```

**Output:**

<img width="906" alt="image" src="https://github.com/user-attachments/assets/c2248e4b-ec6c-4b0d-86a8-d0d15b4b0c88" />


**Question 8**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

```sql
delete from Doctors
where specialization is NULL;
```

**Output:**

<img width="475" alt="image" src="https://github.com/user-attachments/assets/90a1bfbb-308d-400e-88e8-b39b1d3e08a6" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.

```sql
delete from Customer
where GRADE %2 =1;
```

**Output:**

<img width="950" alt="image" src="https://github.com/user-attachments/assets/938af0d2-e13f-45e2-8ce2-47a4d5259177" />


**Question 10**
---
 Write a query to fetch 3 top salaried records from EmployeePosition table.


```sql
select * from EmployeePosition
order by salary desc
limit 3;
```

**Output:**

<img width="671" alt="image" src="https://github.com/user-attachments/assets/690411a0-d15d-4428-af4d-df620dbb53db" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
