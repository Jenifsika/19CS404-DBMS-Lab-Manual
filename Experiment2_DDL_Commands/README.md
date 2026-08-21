# Experiment 2: DDL Commands
## REGISTER NO:212224230019
# NAME: Annie Jenifsika A
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
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
For example:

Test	Result
INSERT INTO Department (DepartmentID, DepartmentName, Location) VALUES (1, 'Human Resources', 'New York');
select * from Department;
DepartmentID  DepartmentName   Location
------------  ---------------  ----------
1             Human Resources  New Y


```
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT NOT NULL UNIQUE,
Location TEXT
);
```

**Output:**

<img width="1428" height="278" alt="image" src="https://github.com/user-attachments/assets/481458c1-72aa-40cb-9fc4-2b264949caa6" />


**Question 2**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER ,
ProjectID INTEGER ,
AssignmentDate DATE NOT NULL,
FOREIGN KEY(EmployeeID)REFERENCES Employees(EmployeeID),
FOREIGN KEY(ProjectID)REFERENCES Projects(ProjectID)
);
```

**Output:**
<img width="1484" height="288" alt="image" src="https://github.com/user-attachments/assets/04eed3be-f8d6-4a1f-bfbd-d76df055a1f0" />


**Question 3**
---

Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).


```sql
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID)REFERENCES Customers(CustomerID));
```

**Output:**

<img width="1356" height="273" alt="image" src="https://github.com/user-attachments/assets/3cf9791b-d17c-4ff4-8bbf-3314928eb638" />


**Question 4**
---
Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

 

```sql
ALTER TABLE employee
ADD COLUMN department_id INTEGER;
ALTER TABLE employee
ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**

<img width="1007" height="233" alt="image" src="https://github.com/user-attachments/assets/3921c77b-5e04-4f79-afb9-ddcdca909865" />


**Question 5**
---
Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values.

```sql
INSERT INTO  Products(ProductID,Name,Category)
VALUES(104,'Tablet','Electronics');
```

**Output:**

<img width="1026" height="194" alt="image" src="https://github.com/user-attachments/assets/3e0460d7-5dc9-4a26-a648-c34af46a10ea" />


**Question 6**
---
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies

```sql
ALTER TABLE Companies
RENAME COLUMN name to first_name;
ALTER TABLE Companies
ADD COLUMN mobilenumber number;
ALTER TABLE Companies
ADD COLUMN DOB Date;
```

**Output:**

<img width="922" height="293" alt="image" src="https://github.com/user-attachments/assets/7a9be798-ed6a-481b-a770-05a5612f22e5" />


**Question 7**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
CREATE TABLE Bonuses(
BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER ,
BonusAmount REAL CHECK(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY (EmployeeID)REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1373" height="214" alt="image" src="https://github.com/user-attachments/assets/67a23d86-b226-4adb-90b6-0644ed01d204" />


**Question 8**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```
sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
DueDate DATE CHECK (DueDate>InvoiceDate),
Amount REAL CHECK(Amount>0)
);
```

**Output:**

<img width="885" height="212" alt="image" src="https://github.com/user-attachments/assets/bedf109c-4608-42e6-8009-65fb49c18c89" />


**Question 9**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql
INSERT INTO Customers(CustomerID,Name,Address,Email)
SELECT * FROM Old_customers;
```

**Output:**

<img width="871" height="239" alt="image" src="https://github.com/user-attachments/assets/bed44c17-1ca8-49bc-8ae4-bcf1f32db9f2" />


**Question 10**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.    

```sql
INSERT INTO  Employee(EmployeeID,Name,Position)
VALUES(4,'Emily White','Analyst');
```


**Output:**

<img width="1191" height="329" alt="image" src="https://github.com/user-attachments/assets/c9d88cc4-14f5-422d-85ae-aa8c8f506205" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
