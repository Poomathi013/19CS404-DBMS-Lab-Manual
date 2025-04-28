# ER Diagram Submission - Student Name

## Scenario Chosen:
University ER Diagram

## ER Diagram:
![ER Diagram](er_diagram.png)![Screenshot (83)](https://github.com/user-attachments/assets/8aff4107-d860-4736-a34b-7ea74a66f9dc)


Entities and Attributes:
```
Student: Name, DOB, Subjects Enrolled, Register Number, Email ID, Phone Number

University: University Name, University ID, Students and Faculties

Department: Department Name, Department ID

Program: Program Name, Program Code, Subjects

Faculty: Name, Subject, Faculty ID

Course: Course Code, Course Name, Credits
```
Relationships and Constraints:
```
Relationship between Student and University ("Relationship")

Cardinality: Many-to-One (M:N)

Participation: Total (each student must belong to a university)

Student is in a Department ("is in a")

Cardinality: Many-to-One (M:N)

Participation: Partial (a student may or may not be associated immediately)

Department provides Program ("provides")

Cardinality: Many-to-Many (M:N)

Participation: Total for Program, Partial for Department

Program contains Course ("contains")

Cardinality: One-to-Many (1:N)

Participation: Total for Course (every course must be in a program)

University has Faculties ("has")

Cardinality: One-to-Many (1:N)

Participation: Partial

Faculty handles Course ("handles")

Cardinality: Many-to-Many (M:N)

Participation: Partial (not all faculties must handle a course immediately)
```
Extension (Prerequisite / Billing):
Prerequisite Modeling:
```
If prerequisites between courses are needed, we can extend by introducing a new relationship "Prerequisite" between Course and Course itself (recursive relationship), indicating one course must be completed before another.
```
Billing Modeling:
```
Billing can be handled by adding an additional entity like Billing with attributes like Student ID, Amount, Due Date, Paid Status. It would have a relationship with Student.
```
Design Choices:
```
I selected Student, Faculty, University, Department, Program, and Course as entities because they represent major objects in any academic environment.

I used M:N relationships for handles and provides because one faculty can handle multiple courses, and one course may need multiple faculties (guest lectures, lab assistants, etc.).

Subjects enrolled is an attribute of Student because it varies per student, rather than as a separate entity to keep it simple.

Recursive extension of Course to model prerequisites is a clean way to manage dependencies without cluttering the original structure.

