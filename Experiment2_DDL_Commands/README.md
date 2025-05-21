# Experiment 2: DDL Commands
# Name: SANJEV R M
# Reference Number: 212223040186
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

create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
CREATE TABLE jobs(
job_id INT,
job_title,
min_salary INT DEFAULT 8000 ,
max_salary NULL);
```

**Output:**
![image](https://github.com/user-attachments/assets/9a4878d2-e59f-498e-8daf-37ea3fad778f)


**Question 2**


Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.
```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES('1','Sarah Parker','Manager','HR','60000');

```

**Output:**
![image](https://github.com/user-attachments/assets/c79c276f-d012-4a3f-b56b-f169db658c6f)

**Question 3**

Insert all products from Discontinued_products into Products.
Table attributes are ProductID, ProductName, Price, Stock

```sql
INSERT INTO Products(ProductID,ProductName,Price,Stock)
SELECT ProductID,ProductName,Price,Stock FROM Discontinued_products;
```

**Output:**
![image](https://github.com/user-attachments/assets/eff71fa6-f416-454c-965e-fb4186b48fbf)



**Question 4**

Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.
```sql
ALTER TABLE Student_details ADD COLUMN Date_of_birth Date;
```

**Output:**

![image](https://github.com/user-attachments/assets/504c4ce7-c06d-4cf0-abcb-ce9262856e3a)

**Question 5**

In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
INSERT INTO Employee(EmployeeID,Name,Position)
VALUES('5','George Clark','Consultant');
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES('7','Noah Davis','Manager','HR','60000');
INSERT INTO Employee(EmployeeID,Name,Position,Department)
VALUES('8','Ava Miller','Consultant','IT');
```

**Output:**
![image](https://github.com/user-attachments/assets/4307d780-6b19-46b1-880e-02c16197ee67)


**Question 6**

Write a SQL query to Add a new column Mobilenumber as number in the Student_details table.

```sql
ALTER TABLE Student_details ADD COLUMN Mobilenumber number;
```

**Output:**
![image](https://github.com/user-attachments/assets/e48fa31e-84fa-42f4-82fb-e0a2c64ca70d)

**Question 7**

Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Shipments(
ShipmentID INT PRIMARY KEY,
ShipmentDate DATE,
SupplierID INT,
OrderID INT,
FOREIGN KEY(SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/2bc28364-bc1e-49ee-8a50-44482f8edbef)

**Question 8**

Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
CREATE TABLE contacts(
contact_id INT PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK(LENGTH(phone)>=10)
);
```

**Output:**
![image](https://github.com/user-attachments/assets/d526bab7-9936-4c28-94a6-b9b142e10220)

**Question 9**

Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INT NOT NULL,
icom_id TEXT(4),
FOREIGN KEY(icom_id) REFERENCES company(com_id)
ON UPDATE SET NULL
ON DELETE SET NULL 
);
```

**Output:**
![image](https://github.com/user-attachments/assets/2517f37b-57a0-4b61-ba2c-8c1dac27fa26)


**Question 10**

Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE
```sql
CREATE TABLE tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**
![image](https://github.com/user-attachments/assets/ab122dad-30d8-4dba-a326-63c562930b80)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
