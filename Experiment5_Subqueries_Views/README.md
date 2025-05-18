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
--
--Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.
```sql
SELECT * FROM GRADES t1
where grade in (select max(grade) from GRADES t2 where t1.subject=t2.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/8613331b-3435-4653-9341-2ba3ea66af0f)


**Question 2**
---
-- From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.
```sql
SELECT * from ORDERS
where purch_amt >(select avg(purch_amt) from ORDERS where ord_date='2012-10-10');
```

**Output:**

![image](https://github.com/user-attachments/assets/e7715a83-cbee-4254-b66f-e45c0764c632)



**Question 3**
--- 
-- Write a SQL query to List departments with names longer than the average length

```sql
SELECT department_id,department_name from Departments
where length(department_name)>(select avg(length(department_name)) from Departments);
```

**Output:**

![image](https://github.com/user-attachments/assets/316d548d-9168-4ca3-8287-90eefb91bdad)



**Question 4**
---
-- Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

```sql
SELECT student_name,grade from GRADES t1
WHERE grade=(select max(grade) from GRADES t2 where t1.subject=t2.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/877a69e1-c808-462d-b340-604e3bfb4d39)



**Question 5**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30

```sql
SELECT * from CUSTOMERS
WHERE ADDRESS='Delhi' and AGE<30
ORDER BY ID;
```

**Output:**

![image](https://github.com/user-attachments/assets/5bdcc345-7699-4086-b233-0376e380a213)



**Question 6**
---
-- Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

```sql
SELECT student_name,grade from GRADES t1
where grade=(select min(grade) from GRADES t2 where t1.subject=t2.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/85302f5c-48d4-4d43-876f-2d7d32e78214)


**Question 7**
---
--Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

```sql
SELECT * from customer
where city<>(select city from customer where id=(select max(id) from customer));
```

**Output:**

![image](https://github.com/user-attachments/assets/ce5023c9-ab4e-4308-8588-cc13a38752f3)


**Question 8**
---
-- Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

```sql
SELECT * FROM customer
where customer_id=(Select salesman_id-2001 from salesman where name='Mc Lyon');
```

**Output:**

![image](https://github.com/user-attachments/assets/fd4c80b8-b24c-4f41-837d-7bc7f307fda6)

**Question 9**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30
```sql
SELECT * from CUSTOMERS
where age<30;
```

**Output:**

![image](https://github.com/user-attachments/assets/6ca96327-eb55-4130-b768-528df2839afd)


**Question 10**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi
```sql
SELECT * FROM CUSTOMERS
WHERE ADDRESS='Delhi';
```

**Output:**

![image](https://github.com/user-attachments/assets/16d988df-1f89-405d-acfe-b74836b1ae64)



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
