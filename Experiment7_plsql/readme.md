# Experiment 6: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
```
SET SERVEROUTPUT ON;

DECLARE
   num1 NUMBER := 80;  -- First number
   num2 NUMBER := 45;  -- Second number
BEGIN
   IF num1 > num2 THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
   END IF;
END;
```
**Expected Output:**  
![image](https://github.com/user-attachments/assets/f608b320-4075-4be8-9a0a-74c79c717710)


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
```
DECLARE
   n     NUMBER := 10;  -- You can change this value
   i     NUMBER := 1;
   sum   NUMBER := 0;
BEGIN
   WHILE i <= n LOOP
      sum := sum + i;
      i := i + 1;
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
```

**Expected Output:**  
![image](https://github.com/user-attachments/assets/bbf8d7c9-dd4c-4fd4-b5b5-7c8067fb006c)

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
```
SET SERVEROUTPUT ON;

SET SERVEROUTPUT ON;

DECLARE
   n   NUMBER := 7;       -- Number of terms
   a   NUMBER := 0;       -- First Fibonacci number
   b   NUMBER := 1;       -- Second Fibonacci number
   c   NUMBER;            -- To store next term
   i   NUMBER := 3;       -- Counter starts from 3 (since first two are printed)
BEGIN
   DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
   DBMS_OUTPUT.PUT_LINE(a);
   DBMS_OUTPUT.PUT_LINE(b);

   WHILE i <= n LOOP
      c := a + b;
      DBMS_OUTPUT.PUT_LINE(c);
      a := b;
      b := c;
      i := i + 1;
   END LOOP;
END;
```
**Expected Output:**  
n = 7  
![image](https://github.com/user-attachments/assets/a2f51d3a-b6ed-4d25-910b-a833d3fdaecd)


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
```
SET SERVEROUTPUT ON;

DECLARE
   n           NUMBER := 1535;   -- Original number
   original_n  NUMBER := 1535;   -- Preserve original for display
   reversed    NUMBER := 0;
   remainder   NUMBER;
BEGIN
   WHILE n > 0 LOOP
      remainder := MOD(n, 10);           -- Get last digit
      reversed := (reversed * 10) + remainder;  -- Build reversed number
      n := TRUNC(n / 10);                -- Remove last digit
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('Original number is: ' || original_n);
   DBMS_OUTPUT.PUT_LINE('Reversed number is: ' || reversed);
END;
/
```

**Expected Output:**  
n = 1535  
Reversed number is 5351
![image](https://github.com/user-attachments/assets/607d034f-9e85-4b43-b190-d2dbaa243918)


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
```
SET SERVEROUTPUT ON;

DECLARE
   a NUMBER := 10;
   b NUMBER := 9;
   c NUMBER := 15;
   largest NUMBER;
BEGIN
   IF a >= b AND a >= c THEN
      largest := a;
   ELSIF b >= a AND b >= c THEN
      largest := b;
   ELSE
      largest := c;
   END IF;

   DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
   DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
```

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15
![image](https://github.com/user-attachments/assets/a03a43fd-795d-45fc-9d21-353404216e8f)



## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
