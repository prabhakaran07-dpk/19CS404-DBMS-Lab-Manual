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
<img width="1112" height="608" alt="image" src="https://github.com/user-attachments/assets/5a5dcc14-61d2-4c24-94b2-50f6b197b435" />


```sql
SELECT 
    customer.cust_name AS "Customer Name", 
    customer.city AS "city", 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    customer
JOIN 
    salesman
ON 
    customer.salesman_id = salesman.salesman_id
WHERE 
    salesman.commission > 0.12;
```

**Output:**

<img width="885" height="467" alt="image" src="https://github.com/user-attachments/assets/1c118a9c-c6bc-44b8-ab8c-ac964554abb6" />


**Question 2**
---
<img width="1333" height="448" alt="image" src="https://github.com/user-attachments/assets/7fcb9ddd-4712-455d-a003-7db11efc3a6a" />


```sql
SELECT 
    patients.date_of_birth, 
    appointments.*
FROM 
    patients
JOIN 
    appointments
ON 
    patients.patient_id = appointments.patient_id
WHERE 
    patients.first_name = 'Alice';
```

**Output:**

<img width="1143" height="220" alt="image" src="https://github.com/user-attachments/assets/a929b498-cfc0-4d44-943f-9eca0c065d1a" />

**Question 3**
---
<img width="890" height="655" alt="image" src="https://github.com/user-attachments/assets/c7df1ef8-bd68-4cd9-9ce4-b4e53b76f6a3" />


```sql
SELECT 
    orders.ord_no, 
    orders.ord_date, 
    orders.purch_amt, 
    customer.cust_name AS "Customer Name", 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    orders
JOIN 
    customer ON orders.customer_id = customer.customer_id
JOIN 
    salesman ON orders.salesman_id = salesman.salesman_id;
```

**Output:**

<img width="1318" height="761" alt="image" src="https://github.com/user-attachments/assets/0bdd1483-7bbf-425b-a8ad-5c18459d527b" />


**Question 4**
---
<img width="1215" height="385" alt="image" src="https://github.com/user-attachments/assets/19590976-5e50-4e3e-8f7d-fdc5bfd48022" />


```sql
SELECT 
    customer.cust_name, 
    customer.city, 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.city AS "city"
FROM 
    customer
JOIN 
    salesman ON customer.salesman_id = salesman.salesman_id
WHERE 
    customer.grade < 300
ORDER BY 
    customer.customer_id ASC;
```

**Output:**

<img width="1026" height="462" alt="image" src="https://github.com/user-attachments/assets/c26b3bf2-cc20-49b1-afdc-ab9744142bfc" />


**Question 5**
---
<img width="1297" height="273" alt="image" src="https://github.com/user-attachments/assets/fd9f1ed3-c0c8-47af-a87f-f4fddef4e5c9" />


```sql
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';
```

**Output:**

<img width="270" height="267" alt="image" src="https://github.com/user-attachments/assets/a238ea57-f265-4d11-b4cb-9327695e212c" />


**Question 6**
---
<img width="971" height="259" alt="image" src="https://github.com/user-attachments/assets/c94e9c9e-e849-4671-abaa-d57e6dac9f4c" />


```sql
SELECT 
    c.cust_name
FROM 
    customer AS c
LEFT JOIN 
    orders AS o ON c.customer_id = o.customer_id;
```

**Output:**

<img width="274" height="759" alt="image" src="https://github.com/user-attachments/assets/4db3d200-bc7c-4d25-bbcc-f1a0fbfeef66" />


**Question 7**
---
<img width="1560" height="360" alt="image" src="https://github.com/user-attachments/assets/c053a535-41ba-49de-a501-24aa67d274e6" />

```sql
SELECT 
    p.first_name AS patient_name, 
    t.*
FROM 
    patients AS p
INNER JOIN 
    test_results AS t ON p.patient_id = t.patient_id;
```

**Output:**
<img width="1370" height="367" alt="image" src="https://github.com/user-attachments/assets/6b2ad7e2-d2e2-49a0-8f7b-21540a3c2943" />


**Question 8**
---
<img width="1154" height="459" alt="image" src="https://github.com/user-attachments/assets/34f270b0-e0f5-416a-bfa9-d2d02320c5d3" />


```sql
SELECT 
    c.cust_name, 
    c.city AS city, 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city
FROM 
    customer c
LEFT JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

<img width="1202" height="657" alt="image" src="https://github.com/user-attachments/assets/66d38639-114a-4ff6-877b-1207556f5d45" />


**Question 9**
---
<img width="1300" height="435" alt="image" src="https://github.com/user-attachments/assets/4db888e9-c240-40d7-8e19-fb3bd39372bb" />


```sql
SELECT 
    p.admission_date, 
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s 
ON 
    p.patient_id = s.patient_id;
```

**Output:**

<img width="555" height="368" alt="image" src="https://github.com/user-attachments/assets/5c8382f5-338d-4299-bb08-dab76d201a39" />


**Question 10**
---
<img width="1041" height="464" alt="image" src="https://github.com/user-attachments/assets/3c796be2-59bf-4c26-9287-3fb47a02832e" />


```sql
SELECT 
    c.cust_name AS "Customer Name", 
    c.city, 
    s.name AS "Salesman", 
    s.commission
FROM 
    customer c
JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1037" height="660" alt="image" src="https://github.com/user-attachments/assets/7ccef3c1-ce9c-4c0e-ac79-a12f3c84e438" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
