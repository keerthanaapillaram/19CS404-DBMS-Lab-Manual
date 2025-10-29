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
How many medical records were created in each month?

Sample table:MedicalRecords Table

<img width="1089" height="164" alt="image" src="https://github.com/user-attachments/assets/fc5a91f4-98f8-4e8c-8e36-691a296248ab" />

```sql
SELECT strftime('%Y-%m', Date) AS Month, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY Month
ORDER BY Month;
```

**Output:**

<img width="574" height="410" alt="image" src="https://github.com/user-attachments/assets/7f4252ca-f1aa-4d7b-b5f5-47cf6a689ec0" />


**Question 2**
---
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

<img width="1089" height="164" alt="image" src="https://github.com/user-attachments/assets/8a3cb9cb-45f4-4a3f-bb84-24eea591a7ad" />


```sql
SELECT PatientID, COUNT(Medications) AS AvgMedications
FROM MedicalRecords GROUP BY PatientID;
```

**Output:**

<img width="610" height="584" alt="image" src="https://github.com/user-attachments/assets/1c029297-daf0-4081-bf14-7efe1f0f8d59" />


**Question 3**
---
How many patients are there in each city?

Sample table: Patients Table


<img width="1076" height="161" alt="image" src="https://github.com/user-attachments/assets/5c992b10-b0cd-4758-84e1-c7084e56c970" />


```sql
SELECT Address, COUNT(PatientID) AS TotalPatients 
FROM Patients
GROUP BY Address;
```

**Output:**


<img width="588" height="381" alt="image" src="https://github.com/user-attachments/assets/2b913407-226f-461e-a6a9-95fa23faae94" />


**Question 4**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders
```
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```

```sql
SELECT COUNT(DISTINCT Salesman_id) COUNT FROM orders;
```

**Output:**


<img width="325" height="291" alt="image" src="https://github.com/user-attachments/assets/070b1f69-75bc-4934-8d15-346cc6331dad" />


**Question 5**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee
```
name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```

```sql
SELECT COUNT(id) AS employees_count FROM employee WHERE income > 50000;
```

**Output:**


<img width="411" height="295" alt="image" src="https://github.com/user-attachments/assets/0f23429e-5cd1-4efb-908e-440ccdfb28cf" />


**Question 6**
---
Write a SQL query to find the average length of email addresses (in characters):

Table: customer
```
name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
```

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length FROM customer;
```

**Output:**


<img width="419" height="278" alt="image" src="https://github.com/user-attachments/assets/6e36c291-bb5d-459e-891b-1c6506946e98" />


**Question 7**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee
```
name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```

```sql
SELECT SUM(income) AS total_income FROM employee WHERE age >= 40;
```

**Output:**


<img width="356" height="290" alt="image" src="https://github.com/user-attachments/assets/47101bff-5d07-463b-b4b7-738890dd35e0" />


**Question 8**
---
Write the SQL query that performs grouping by age groups and displays the maximum salary for each group, excluding groups where the maximum salary is not greater than 8000. 

Note: Calculate the age group as multiples of 5.

Eg., 20,22,23 comes in age group 20. 

25,27,29 comes in age group 25.

Sample table: customer1


<img width="992" height="173" alt="image" src="https://github.com/user-attachments/assets/26b22200-eb50-4cb2-bae6-d74eccf98bd5" />


```sql
SELECT (age/5) * 5 AS age_group, MAX(salary)
FROM customer1
GROUP BY age_group
HAVING MAX(salary) > 8000;
```

**Output:**

<img width="558" height="336" alt="image" src="https://github.com/user-attachments/assets/7f5f40a7-5679-486b-9179-24aef34b8fd9" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

Sample table: customer1


<img width="992" height="173" alt="image" src="https://github.com/user-attachments/assets/3d9c04d2-a6fc-4000-a578-6ffbcf14bb01" />


```sql
SELECT address, SUM(salary) FROM customer1 GROUP BY address HAVING SUM(salary) > 2000;
```

**Output:**


<img width="553" height="457" alt="image" src="https://github.com/user-attachments/assets/3ade07ae-b584-4251-90a0-225b4989e841" />


**Question 10**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

Sample table: products


<img width="972" height="212" alt="image" src="https://github.com/user-attachments/assets/da93752e-b24d-4aa5-b4d9-0db86c4c1ca3" />

```sql
SELECT category_id, SUM(price) AS Total_Cost FROM products GROUP BY category_id HAVING Total_Cost > 50;
```

**Output:**

<img width="555" height="309" alt="image" src="https://github.com/user-attachments/assets/fc845827-4f6d-4a21-a9fa-c421ee4f5849" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
