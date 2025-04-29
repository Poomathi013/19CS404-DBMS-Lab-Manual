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
Write a SQL query to Add a new column Country as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
For example:

Test	Result
pragma table_info('Student_details');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      int         0                       1
1           Name        VARCHAR(10  1                       0
2           Gender      TEXT        1                       0
3           Subject     VARCHAR(30  0                       0
4           MARKS       INT (3)     0                       0
5           Country     TEXT        0                       0


```sql
ALTER TABLE Student_Details ADD COLUMN Country TEXT
```

**Output:**

<img width="924" alt="image" src="https://github.com/user-attachments/assets/8f972497-17c3-4b28-87d6-179905f03fbc" />


**Question 2**
---
Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER
For example:

Test	Result
pragma table_info('Orders');
cid   name        type        notnull     dflt_value  pk
----  ----------  ----------  ----------  ----------  ----------
0     OrderID     INTEGER     0                       0
1     OrderDate   TEXT        0                       0
2     CustomerID  INTEGER     0                       0


```sql
CREATE TABLE Orders(
    OrderID INTEGER,
    OrderDate TEXT,
    CustomerID INTEGER
    );
    
```

**Output:**

<img width="947" alt="image" src="https://github.com/user-attachments/assets/82fd42ce-e39d-4cc7-adfe-2b61e226461f" />


**Question 3**
---
Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

ISBN             Title                 Author
---------------  --------------------  ---------------
978-6655443321   Big Data Analytics    Karen Adams

Note: The Publisher and Year columns will use their default values.
 
 
For example:

Test	Result
SELECT ISBN, Title, Author
FROM Books 
ISBN             Title                 Author
---------------  --------------------  ---------------
978-6655443321   Big Data Analytics    Karen Adams

```sql
INSERT INTO  Books(ISBN,Title,Author)
VALUES("978-6655443321","Big Data Analytics","Karen Adams")
```

**Output:**

<img width="877" alt="image" src="https://github.com/user-attachments/assets/c31b0bee-53f5-48fe-9290-90277390481c" />


**Question 4**
---
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
For example:

Test	Result
SELECT Name, Category, Price, Stock FROM Products;

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300

```sql
INSERT INTO products(Name,Category,Price,Stock)
VALUES("Smartphone","Electronics",800,150);
INSERT INTO products(Name,Category,Price,Stock)
VALUES("Headphones","Accessories",200,300);
```

**Output:**

<img width="899" alt="image" src="https://github.com/user-attachments/assets/dcf930a0-bb68-4597-a731-8862b01139a4" />


**Question 5**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
For example:

Test	Result
INSERT INTO Invoices (InvoiceID, InvoiceDate)
VALUES (1, '2024-08-08'),(1,'2024-09-08');
Error: UNIQUE constraint failed: Invoices.InvoiceID

```sql
CREATE TABLE Invoices(
    InvoiceID INTEGER primary key,
    InvoiceDate DATE,
    DueDate DATE CHECK(DUEDATE>InvoiceDate),
    Amount REAL CHECK(AMOUNT>0)
    );
```

**Output:**

<img width="830" alt="image" src="https://github.com/user-attachments/assets/2b5960b4-6393-47a2-a2fc-79018dcf7d49" />


**Question 6**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.
For example:

Test	Result
INSERT INTO ProjectAssignments (AssignmentID, EmployeeID, ProjectID, AssignmentDate) VALUES (2, 99, 1, '2024-01-03');
Error: FOREIGN KEY constraint failed


```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER primary key,
    EmployeeID INTEGER ,
    ProjectID INTEGER, 
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
    );
```

**Output:**

<img width="898" alt="image" src="https://github.com/user-attachments/assets/01738956-20c9-4f79-9834-d895ae23f15e" />


**Question 7**
---
Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
For example:

Test	Result
select * from student_details;
RollNo      Name           Gender      Subject     MARKS
----------  -------------  ----------  ----------  ----------
1           Alice Johnson  Female      Math        85
2           Bob Smith      Male        Science     90
3           Charlie Brown  Male        English     78

```sql
INSERT INTO student_details(RollNo,Name,Gender,Subject,MARKS)
SELECT RollNo,Name,Gender,Subject,MARKS
FROM Archived_students;

```

**Output:**

<img width="939" alt="image" src="https://github.com/user-attachments/assets/2ec873a7-10b3-457f-ad8f-d147dba6356f" />


**Question 8**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.
For example:

Test	Result
INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;
item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700

```sql
CREATE TABLE item(
    item_id TEXT Primary keY,
    item_desc TEXT,
    rate INTEGER,
    icom_id TEXT(4), 
    FOREIGN KEY (icom_id) REFERENCES company(com_id)
    ON UPDATE SET NULL
    ON DELETE SET NULL
    );

```

**Output:**

<img width="872" alt="image" src="https://github.com/user-attachments/assets/fedb649d-c512-4d35-8d2d-9bbab5ab6d5b" />


**Question 9**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0
For example:

Test	Result
INSERT INTO products (product_id, product_name, list_price) VALUES (2, 'Product B', 50.00);
SELECT * FROM products;
product_id  product_name  list_price  discount
----------  ------------  ----------  ----------
2           Product B     50          0

```sql
CREATE TABLE products(
   product_id INTEGER primary key,
   product_name TEXT not NULL,
   list_price DECIMAL (10, 2) not NULL,
   discount DECIMAL (10, 2) default 0 not NULL,
   CHECK (list_price>=discount),
   CHECK (discount>=0), 
   CHECK (list_price>=0)
   );
```

**Output:**

<img width="941" alt="image" src="https://github.com/user-attachments/assets/37deb341-8b1a-44e8-9bd5-9be62b14a8f5" />

**Question 10**
---
Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).

For example:

Test	Result
pragma table_info('employee');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           salary      number      0                       0
2           designatio  varchar(50  0                       0


```sql
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**

<img width="951" alt="image" src="https://github.com/user-attachments/assets/44ee0419-8db1-4b47-97bb-20b3f553b5b0" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
