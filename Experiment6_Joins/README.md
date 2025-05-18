# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of all columns from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers with the name 'Fabian Johns'.
```sql
SELECT s.* from salesman s 
left join customer c on c.salesman_id=s.salesman_id
where c.cust_name ='Fabian Johns';
```

**Output:**
![image](https://github.com/user-attachments/assets/ecab3803-ce5c-4a03-86bb-90523192ce59)


**Question 2**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for customers with a grade less than or equal to 100.
```sql
SELECT s.name,c.cust_name,c.city,c.grade,c.salesman_id from salesman s
left join customer c on c.salesman_id=s.salesman_id
where c.grade<=100;
```

**Output:**
![image](https://github.com/user-attachments/assets/5ff4c305-06be-49c3-b14b-64f93c6dda21)



**Question 3**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount less than 100.

```sql
SELECT c.cust_name from customer c
left join orders o on c.customer_id=o.customer_id
where o.purch_amt<100;
```

**Output:**
![image](https://github.com/user-attachments/assets/642817f5-9d74-434f-b052-fa3a9280fe2f)



**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column. Include conditions to filter for patients discharged between '2024-03-01' and '2024-03-31' but not admitted during the same period.

```sql
SELECT p.first_name,s.* from patients p
inner join surgeries s on p.patient_id=s.patient_id
where p.discharge_date between '2024-03-01' and '2024-03-31';
```

**Output:**

![image](https://github.com/user-attachments/assets/e265873a-7246-4d62-8da5-5e42c31aeabc)


**Question 5**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c") and the "commission" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column.

```sql
select c.cust_name,s.commission from customer c
left join salesman s on c.salesman_id=s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/0e522200-790c-4ff8-9587-f0424ce07ddc)


**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test name 'X-Ray' and a result of 'Normal'.

```sql
SELECT p.* from patients p
inner join test_results t on p.patient_id=t.patient_id
where t.test_name='X-Ray' and t.result='Normal';
```

**Output:**

![image](https://github.com/user-attachments/assets/d1d00087-777c-403c-ac2a-d36d17b0988f)


**Question 7**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```sql
SELECT o.ord_no,o.purch_amt,c.cust_name,c.city from orders o
join customer c on c.customer_id=o.customer_id
where o.purch_amt between 500 and 2000;
```

**Output:**
![image](https://github.com/user-attachments/assets/6f8cb0a1-b756-4622-b6c0-02bc0cd82064)


**Question 8**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.

```sql
SELECT p.first_name as patient_name,d.first_name as doctor_name from patients p
inner join doctors d on p.doctor_id=d.doctor_id
where p.date_of_birth>'1990-01-01';
```

**Output:**
![image](https://github.com/user-attachments/assets/8adab6de-560c-47ed-800c-09ab6a8db4e5)



**Question 9**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a null discharge date.
```sql
SELECT p.first_name as patient_name,d.first_name as doctor_name from patients p
inner join doctors d on p.doctor_id=d.doctor_id
where p.discharge_date IS NULL;
```

**Output:**
![image](https://github.com/user-attachments/assets/db567179-a59e-4b49-b3f4-ec2d4a6455ce)


**Question 10**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 
```sql
SELECT o.ord_no,o.ord_date,o.purch_amt,c.cust_name as "Customer Name",c.grade,s.name as "Salesman",s.commission
from orders o
join customer c on o.customer_id=c.customer_id
join salesman s on o.salesman_id=s.salesman_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/d31199f5-e4dd-4004-bedc-15f12aea82ef)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
