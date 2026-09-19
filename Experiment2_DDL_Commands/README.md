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
<img width="1187" height="307" alt="image" src="https://github.com/user-attachments/assets/02523f42-70e5-43fb-9036-116ae0b755e8" />


```sql

INSERT INTO Employee(EmployeeID,Name,Position)
values(5,           'George Clark',  'Consultant');

INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
values(7,           'Noah Davis',    'Manager',     'HR',          60000);

INSERT INTO Employee(EmployeeID,Name,Position,Department)
values(8,           'Ava Miller',    'Consultant',  'IT');
```

**Output:**

<img width="1253" height="175" alt="image" src="https://github.com/user-attachments/assets/06724fd4-39d5-49ab-a1fe-6f336d639172" />


**Question 2**
---
<img width="1221" height="406" alt="image" src="https://github.com/user-attachments/assets/24817168-235a-495d-b53d-b90e6fb5cfe9" />


```sql
CREATE TABLE Attendance (  
    AttendanceID INTEGER PRIMARY KEY,  
    EmployeeID INTEGER,  
    AttendanceDate DATE,  
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),  
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)  
);
```

**Output:**

<img width="1247" height="382" alt="image" src="https://github.com/user-attachments/assets/f7aa65e9-029f-4925-b383-fbc01ba789e6" />


**Question 3**
---
<img width="1140" height="358" alt="image" src="https://github.com/user-attachments/assets/2873c3e2-ad0e-4549-8e9e-aee8db2bc985" />

```sql
--
ALTER TABLE Employees
ADD COLUMN Date_of_joining Date;

ALTER TABLE Employees
RENAME COLUMN job_title To Designation;


```

**Output:**

<img width="1220" height="415" alt="image" src="https://github.com/user-attachments/assets/3823d689-0bfb-4bc7-9035-e22180f4d708" />


**Question 4**
---
<img width="1394" height="349" alt="image" src="https://github.com/user-attachments/assets/9d785d14-817b-4e52-9869-18a90daa98da" />


```sql
--
 CREATE TABLE jobs (  
    job_id INTEGER PRIMARY KEY,  
    job_title TEXT NOT NULL DEFAULT '',  
    min_salary INTEGER NOT NULL DEFAULT 8000,  
    max_salary INTEGER DEFAULT NULL  
);
```

**Output:**

<img width="1252" height="434" alt="image" src="https://github.com/user-attachments/assets/258f1e41-98df-4a8e-a0e9-bc44889e0ee7" />


**Question 5**
---
<img width="1485" height="381" alt="image" src="https://github.com/user-attachments/assets/0d7624f7-24b9-4d42-be84-ec919d5d9d19" />


```sql
--
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**

<img width="1236" height="442" alt="image" src="https://github.com/user-attachments/assets/4db6a1da-b70d-4bae-b30e-a8548e8aff83" />


**Question 6**
---
<img width="1063" height="350" alt="image" src="https://github.com/user-attachments/assets/e9ac6068-fb67-408f-802e-94b3144fdff3" />


```sql
--
select *from Out_of_print_books
union all
select *from Books
```

**Output:**

<img width="1229" height="380" alt="image" src="https://github.com/user-attachments/assets/b4264ad8-cc16-47bd-8e31-1597b189588f" />


**Question 7**
---
<img width="1075" height="454" alt="image" src="https://github.com/user-attachments/assets/d1333328-6de6-45e1-ba39-c3aa35660665" />


```sql
--
CREATE TABLE item (  
    item_id TEXT PRIMARY KEY,  
    item_desc TEXT NOT NULL,  
    rate INTEGER NOT NULL,  
    icom_id TEXT CHECK(4),  
    FOREIGN KEY (icom_id) REFERENCES company(com_id)  
    ON UPDATE CASCADE  
    ON DELETE CASCADE  
);
```

**Output:**
<img width="1236" height="438" alt="image" src="https://github.com/user-attachments/assets/2c63a22c-a9cb-4833-9cad-0af8c7e08af3" />


**Question 8**
---
<img width="1099" height="297" alt="image" src="https://github.com/user-attachments/assets/963e910e-2688-448e-9a77-e53d5e39f4f7" />


```sql
--
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**

<img width="1242" height="375" alt="image" src="https://github.com/user-attachments/assets/32261511-df13-4836-8f4d-14f1d8e95e7e" />


**Question 9**
---
<img width="1243" height="289" alt="image" src="https://github.com/user-attachments/assets/b2a19dc7-72f7-4116-a711-eb6cabdb701c" />


```sql
--
INSERT INTO Products (ProductID, Name, Category)  
VALUES (104, 'Tablet', 'Electronics');
```

**Output:**

<img width="1270" height="326" alt="image" src="https://github.com/user-attachments/assets/e2105c87-2b7a-4bdc-bcf3-fb5a6000b89d" />


**Question 10**
---
<img width="1232" height="396" alt="image" src="https://github.com/user-attachments/assets/767f4828-9916-402f-b19c-e8ef9c7b1dcf" />


```sql
--
CREATE TABLE Employees(
EmployeeID INTEGER primary key,
FirstName INTEGER NOT NULL,
LastName INTEGER NOT NULL,
Email VARCHAR(50) unique,
Salary CHECK (Salary>0),
DepartmentID INTEGER,
foreign key(DepartmentID) references Departments(DepartmentID)
);
```

**Output:**

<img width="1234" height="488" alt="image" src="https://github.com/user-attachments/assets/a7c281e7-b07d-4fd3-ae3b-1e15861fd547" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
