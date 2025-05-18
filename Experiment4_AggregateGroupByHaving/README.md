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
-- Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

```sql
SELECT COUNT(DISTINCT salesman_id) as COUNT from orders
```

**Output:**
![image](https://github.com/user-attachments/assets/a74663e0-9655-4621-819e-b6d7dee7f419)


**Question 2**
---
--Write a SQL query to find the shortest email address in the customer table?

```sql
SELECT name,email,MIN(LENGTH(email)) as min_email_length
from customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/515e110f-135c-44cd-8088-4de2ece3390c)


**Question 3**
---
-- How many male and female doctors are there in each medical specialty?
```sql
select Specialty,Gender,count(DoctorID) as TotalDoctors from Doctors
group by Specialty,Gender;
```

**Output:**
![image](https://github.com/user-attachments/assets/ce4c3f05-a23e-4ce3-89ed-a483e0cf2409)


**Question 4**
---
-- Write SQL query to extract the email domain from each patient's email address and count the number of patients with the same email domain.

```sql
SELECT SUBSTR(Email,INSTR(Email,'@')+1) AS EmailDomain,Count(*) as TotalPatients
from Patients
group by EmailDomain;
```

**Output:**


![image](https://github.com/user-attachments/assets/4da63f66-53d1-4cd7-b990-39ba4b8ede6d)


**Question 5**
---
-- Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.
```sql
SELECT age,MAX(income) from employee
group by age
having MAX(income)>2000000;
```

**Output:**


![image](https://github.com/user-attachments/assets/27c85f23-a05b-4a45-b116-68c61d4e4197)


**Question 6**
---
--Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.
```sql
SELECT (age/5)*5 as age_group,SUM(salary) from customer1
group by (age/5)*5
having sum(salary)>5000;
```

**Output:**
![image](https://github.com/user-attachments/assets/52798270-7a61-45fb-9bb8-f0b4653366e4)


**Question 7**
---
--Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

```sql
SELECT (age/5)*5 as age_group,AVG(age) 
from customer1
group by (age/5)*5
having AVG(age) <24;
```

**Output:**

![image](https://github.com/user-attachments/assets/4de42af7-81a0-4eaf-9d75-9139919772ed)


**Question 8**
---
--|Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

```sql
SELECT COUNT(*) as COUNT FROM Customer
where city='Noida';
```

**Output:**

![image](https://github.com/user-attachments/assets/3e389da2-5f42-4e98-8d46-8a25bc40d124)


**Question 9**
---
-- What is the most common diagnosis among patients?

```sql
SELECT Diagnosis,count(*) as DiagnosisCount from MedicalRecords 
Group BY Diagnosis
order by DiagnosisCount DESC
LIMIT 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/03e6a49c-ca73-4212-bf92-f55317995d07)


**Question 10**
---
--Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.
```sql
SELECT category_id,min(Price) as Price  from products
group by category_id
having min(Price)<10;
```

**Output:**


![image](https://github.com/user-attachments/assets/6bd36c31-da15-4a55-8da3-a11e758b7cf3)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
