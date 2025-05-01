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
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).



```
CREATE TABLE Orders(OrderID INTEGER PRIMARY KEY,OrderDate DATE NOT NULL,CustomerID INTEGER, FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID));

```


**Output:**

![image](https://github.com/user-attachments/assets/7986dd47-7996-481f-9783-b7d3b953f141)


**Question 2**
---
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
 ALTER TABLE Customer ADD COLUMN birth_date timestamp;
```

**Output:**

![image](https://github.com/user-attachments/assets/1a6aff6e-8bd5-4ebb-b54b-43dce631b128)


**Question 3**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).


```
CREATE TABLE Invoices(InvoiceID INTEGER PRIMARY KEY,InvoiceDate DATE,Amount REAL CHECK(Amount>0),DueDate DATE CHECK(DueDate>InvoiceDate),
OrderID INTEGER, FOREIGN KEY(OrderID) REFERENCES Orders(OrderID));

```

**Output:**

![image](https://github.com/user-attachments/assets/a40d3a53-5b22-436d-81ae-34f409d0a48b)


**Question 4**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

For example:

Test	Result
SELECT * FROM Books;
ISBN            Title                    Author      Publisher   Year
--------------  -----------------------  ----------  ----------  ----------
978-1234567890  Data Science Essentials  Jane Doe    TechBooks   2024

```sql

INSERT INTO Books(ISBN,Title,Author,Publisher,Year) values ( '978-1234567890',
'Data Science Essentials','Jane Doe','TechBooks',2024);

```

**Output:**

![image](https://github.com/user-attachments/assets/fabf5756-f7c7-4be0-a646-860c0ea5a723)


**Question 5**
---
Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql

ALTER TABLE Customer ADD COLUMN email VARCHAR(100);
```

**Output:**

![image](https://github.com/user-attachments/assets/d56e70f4-284e-472d-9d1e-3ed216a16ba8)


**Question 6**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
CREATE TABLE jobs(job_id INTEGER,job_title VARCHAR(50) ,min_salary INTEGER DEFAULT 8000 ,max_salary NULL);

```

**Output:**

![image](https://github.com/user-attachments/assets/0431eec9-745d-44dc-9ae3-0c6655a6a847)

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
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
SELECT RollNo,Name,Gender,Subject,MARKS FROM Archived_students;

```

**Output:**

![image](https://github.com/user-attachments/assets/cdcaef0b-2e24-4f3e-81b1-dd599360a1ca)


**Question 8**
---Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
CREATE TABLE Members(MemberID INTEGER,MemberName TEXT,JoinDate DATE);

```

**Output:**

![image](https://github.com/user-attachments/assets/135b0c44-75bf-4292-85af-6a0fbccaf398)


**Question 9**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001


```sq
lINSERT INTO Customers(CustomerID,Name,Address,City,Zipcode)values(302,'Laura Croft','456 Elm St','Seattle',98101);
INSERT INTO Customers(CustomerID,Name,Address,City,Zipcode)values(303,'Bruce Wayne','789 Oak St','Gotham',10001);
```

**Output:**

![image](https://github.com/user-attachments/assets/3c324482-7000-4ab8-88e7-42aabeb9d729)


**Question 10**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
CREATE TABLE Bonuses(BonusID INTEGER PRIMARY KEY,EmployeeID INTEGER,BonusAmount REAL 
CHECK (BonusAmount>0),BonusDate DATE,Reason TEXT NOT NULL,FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID));
```

**Output:**

![image](https://github.com/user-attachments/assets/f9d14f54-fbc2-4cc7-b962-43e712ef0da4)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
