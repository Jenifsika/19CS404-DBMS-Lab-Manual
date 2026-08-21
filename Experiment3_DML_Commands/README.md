# Experiment 3: DML Commands
# REGISTER NO: 212224230019
# NAME: Annie Jenifsika A
## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
<img width="894" height="527" alt="image" src="https://github.com/user-attachments/assets/6641dd68-b54e-40d1-9cc9-1221244f9cc1" />


```sql
SELECT customer_id,cust_name,city,grade,salesman_id
FROM customer
WHERE city='New York' OR grade<=100;
```

**Output:**

<img width="814" height="250" alt="image" src="https://github.com/user-attachments/assets/0eaecdd3-a5ba-409f-8537-cc6da954fe9a" />


**Question 2**
---
<img width="866" height="406" alt="image" src="https://github.com/user-attachments/assets/8b5fee27-08c6-419e-a2b7-e9df9cd22f68" />


```sql
SELECT first_name,last_name,
CASE
WHEN (strftime('%Y','2023-12-30')-strftime('%Y',date_of_birth))<20 THEN 'Under 20'
WHEN (strftime('%Y','2023-12-30')-strftime('%Y',date_of_birth))BETWEEN 20 AND 30 THEN '20-30'
WHEN (strftime('%Y','2023-12-30')-strftime('%Y',date_of_birth))BETWEEN 31 AND 40 THEN '31-40'
WHEN (strftime('%Y','2023-12-30')-strftime('%Y',date_of_birth))BETWEEN 41 AND 50 THEN '41-50'
ELSE 'Above 50'
END AS AgeGroup
FROM Patients;

```

**Output:**

<img width="881" height="504" alt="image" src="https://github.com/user-attachments/assets/e9f79d36-c0f8-4131-865e-7a5871f5d2a5" />


**Question 3**
---
<img width="876" height="519" alt="image" src="https://github.com/user-attachments/assets/0f8eb894-b93d-4b7a-9561-691e450dc6bd" />


```sql
DELETE FROM Doctors
WHERE (specialization='Pediatrics'OR specialization='Cardiology')
AND last_name='Brown';
```

**Output:**
<img width="776" height="500" alt="image" src="https://github.com/user-attachments/assets/8c6b66fc-b554-4d1c-b61a-fb24938c0fdf" />


**Question 4**
---
<img width="909" height="495" alt="image" src="https://github.com/user-attachments/assets/f1f33215-6756-4158-bb9e-519c5f3d56db" />


```sql
SELECT product_id,original_price,discount_percentage,
original_price*(1-discount_percentage)AS discounted_price
FROM Products;
```

**Output:**
<img width="765" height="220" alt="image" src="https://github.com/user-attachments/assets/80761b79-fbf3-42dd-9b2d-e1ff747e3977" />


**Question 5**
---
<img width="897" height="324" alt="image" src="https://github.com/user-attachments/assets/8ed49a30-0ae2-41a8-98c1-910abb0a93a6" />


```sql
UPDATE sales
set sell_price=sell_price*1.05
WHERE product_id=15 AND sale_date='2023-01-31';
```

**Output:**
<img width="1013" height="254" alt="image" src="https://github.com/user-attachments/assets/30bd5a4f-e038-4c26-968c-c7834311aad7" />


**Question 6**
---
<img width="879" height="240" alt="image" src="https://github.com/user-attachments/assets/f85ad262-e00c-49b6-8ea2-e87df24668bc" />


```sql
SELECT *
FROM EmployeeInfo
WHERE Address='Delhi(DEL)';
```

**Output:**
<img width="979" height="189" alt="image" src="https://github.com/user-attachments/assets/1253d417-e737-4acb-93ca-133e5dcf3d47" />


**Question 7**
---
<img width="858" height="459" alt="image" src="https://github.com/user-attachments/assets/665a6973-2845-4e6c-a742-59ea061b637b" />


```sql
UPDATE Employees
Set salary=salary*2
WHERE department_id=20 AND job_id LIKE'%MAN';
```

**Output:**
<img width="1066" height="216" alt="image" src="https://github.com/user-attachments/assets/690b2c6c-9936-4041-b2f2-cfa015fa3764" />


**Question 8**
---
<img width="922" height="380" alt="image" src="https://github.com/user-attachments/assets/6526c056-dad7-4da1-9252-c81ba4acebeb" />


```sql
SELECT ename,job,Substr(ename,1,3)||Substr(job,-3)AS ConcatenatedString
FROM emp;
```

**Output:**
<img width="646" height="354" alt="image" src="https://github.com/user-attachments/assets/eca0a108-2003-4982-875c-f353840d670e" />


**Question 9**
---
<img width="893" height="352" alt="image" src="https://github.com/user-attachments/assets/5285e739-5e47-458c-98ee-642d0233e4a0" />


```sql
Update products
set sell_price=sell_price*1.10
WHERE category='Bakery';
```

**Output:**
<img width="1144" height="190" alt="image" src="https://github.com/user-attachments/assets/b7ad338d-d09c-4f63-8f80-0489455e954b" />


**Question 10**
---
<img width="880" height="303" alt="image" src="https://github.com/user-attachments/assets/75fdef97-5c3b-4a9f-9a84-f5aaa199f5f5" />


```sql
SELECT *
FROM EmployeeInfo
WHERE EmpLname LIKE'____A';
```

**Output:**
<img width="1374" height="302" alt="image" src="https://github.com/user-attachments/assets/d5026406-5c75-4637-b250-48813c39546a" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
