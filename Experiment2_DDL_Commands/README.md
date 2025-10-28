# Experiment 2: DDL Commands
```
Developed by;
Name : P Keerthana
Reg No : 212223240069
```

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
![image](https://github.com/user-attachments/assets/50a79907-17ad-4021-bf11-27706a720b31)

**Program:**
```sql
ALTER TABLE employee ADD COLUMN designation varchar(50);
```

**Output:**

![image](https://github.com/user-attachments/assets/dce27374-26db-472d-8dfc-50191676368f)


**Question 2**
---
![image](https://github.com/user-attachments/assets/d7529bd6-c253-48dc-9749-491421c14344)

**Program:**
```sql
CREATE TABLE Employees(EmployeeID INTEGER,FirstName TEXT,LastName TEXT,HireDate DATE);
```

**Output:**

![image](https://github.com/user-attachments/assets/90dcffb9-5a9e-487a-b11f-6038208848a8)


**Question 3**
---
![image](https://github.com/user-attachments/assets/0456c687-aa34-4c33-b52e-43f1e1d1f776)

**Program:**
```sql
CREATE TABLE Locations(LocationID INTEGER,LocationName TEXT,Address TEXT);
```

**Output:**

![image](https://github.com/user-attachments/assets/3e255c2b-83e8-4468-83f3-dcdb20c3b71e)


**Question 4**
---
![image](https://github.com/user-attachments/assets/c608e8a2-4a4c-4abc-a9eb-488c84a2b6ed)

**Program:**
```sql
CREATE TABLE Members(MemberID INTEGER,MemberName TEXT,JoinDate DATE);
```

**Output:**
![image](https://github.com/user-attachments/assets/6035ad29-6160-4a43-9a71-359a29c6b617)


**Question 5**
---
![image](https://github.com/user-attachments/assets/0a80f8fc-747c-4451-8cf8-9594a9680acf)

**Program:**
```sql
INSERT INTO Products(ProductID,Name,Category,Price,Stock) VALUES (101,'Laptop','Electronics',1500,50);
```

**Output:**

![image](https://github.com/user-attachments/assets/1f77bbfd-4bd1-40d2-ba50-72ff20766a9e)


**Question 6**
---
![image](https://github.com/user-attachments/assets/1aa07b34-e803-47d7-8318-8a169baf3980)

**Program:**
```sql
ALTER TABLE Student_details ADD COLUMN Date_of_birth Date;
```

**Output:**
![image](https://github.com/user-attachments/assets/83df0769-64e4-4ebc-b66d-2273f3b16b44)


**Question 7**
---
![image](https://github.com/user-attachments/assets/d3ea3569-6466-4b8c-bd6c-659f6fb73f68)

**Program:**
```sql
CREATE TABLE Products(
    ProductID PRIMARY KEY,
    ProductName NOT NULL,
    Price REAL CHECK(Price>0),
    Stock INTEGER CHECK(Stock>=0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/9c116bcd-5018-4481-8fd2-2f2752c4bb53)


**Question 8**
---
![image](https://github.com/user-attachments/assets/58b8f24c-d473-4eff-b276-d4c6f2433efa)

**Program:**
```sql
INSERT INTO Student_details (RollNo,Name,Gender) VALUES (204,'Samuel Black','M');
```

**Output:**

![image](https://github.com/user-attachments/assets/0380f08a-8741-4c82-b5c3-15e9cd327c89)


**Question 9**
---
![image](https://github.com/user-attachments/assets/6d9a1185-c523-4ebf-a97e-5363fb8c459a)

**Program:**
```sql
CREATE TABLE Attendance(
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present','Absent','Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
    );
```

**Output:**
![image](https://github.com/user-attachments/assets/f1471ac5-96db-4d5d-971e-d948c41397c2)

**Question 10**
---
![image](https://github.com/user-attachments/assets/fae2bd83-5291-469c-9806-b093de59c950)

**Program:**
```sql
INSERT INTO Products(Name,Category,Price,Stock) VALUES ('Smartphone','Electronics',800,150),('Headphones','Accessories',200,300);
```

**Output:**

![image](https://github.com/user-attachments/assets/f618a7eb-fc94-44f7-9b18-51df9752c22a)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

## Module Completion
![image](https://github.com/user-attachments/assets/31010aa8-f7dd-447a-9bf1-f6f53a58517c)

