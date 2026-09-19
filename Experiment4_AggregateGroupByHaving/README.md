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
-- How many appointments are scheduled for each patient?

```sql
SELECT PatientID , count(AppointmentID) as TotalAppointments
FROM Appointments 
group by PatientID
ORDER BY PatientID
```

**Output:**
<img width="693" height="635" alt="image" src="https://github.com/user-attachments/assets/21cc883e-469e-42fa-9ce0-c7ad4c8c1214" />


**Question 2**
---
-- What is the average duration of insurance coverage for patients covered by each insurance company?

```sql
SELECT InsuranceCompany, AVG(enddate - startdate) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**
<img width="955" height="684" alt="image" src="https://github.com/user-attachments/assets/6a6f4b9a-4714-4882-999c-4c8bfa3b81c4" />


**Question 3**
---
-- How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

```sql
select Frequency, count(PatientID) as TotalPrescriptions
FROM Prescriptions
group by Frequency;
```

**Output:**
<img width="786" height="530" alt="image" src="https://github.com/user-attachments/assets/bddaadf1-f259-430b-ab90-a204bdc1ac21" />


**Question 4**
---
-- Write a SQL query to find the average salary of all employees?

```sql
SELECT AVG(income) AS Average_Salary 
FROM employee;
```

**Output:**

<img width="500" height="311" alt="image" src="https://github.com/user-attachments/assets/2f9a89d8-61aa-48fc-b06d-9f3f4baa2e29" />


**Question 5**
---
-- Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

```sql
SELECT count(distinct salesman_id) AS COUNT
FROM orders;
```

**Output:**

<img width="399" height="316" alt="image" src="https://github.com/user-attachments/assets/58219eeb-a867-4e0c-944a-8758fc858519" />

**Question 6**
---
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

```sql
SELECT COUNT(id) AS COUNT FROM customer 
WHERE city != 'Noida';
```

**Output:**
<img width="394" height="311" alt="image" src="https://github.com/user-attachments/assets/200be541-c1d1-49d2-a03d-3a3ab1e55fe7" />



**Question 7**
---
-- Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

```sql
SELECT MAX(age) - MIN(age) AS age_difference 
FROM employee;
```

**Output:**

<img width="458" height="312" alt="image" src="https://github.com/user-attachments/assets/2d574d76-3e7f-4aa6-a13b-c09acc793dd4" />


**Question 8**
---
--Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

```sql
SELECT jdate, MIN(workhour) 
FROM employee1 
GROUP BY jdate 
HAVING MIN(workhour) < 10;
```

**Output:**

<img width="656" height="379" alt="image" src="https://github.com/user-attachments/assets/8dcbb7d5-62d4-4435-9e3d-6f3e2270cf61" />



**Question 9**
---
-- Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

```sql
SELECT jdate, SUM(workhour)
FROM employee1 
GROUP BY jdate
HAVING SUM(workhour) >= 40;
```

**Output:**

<img width="636" height="373" alt="image" src="https://github.com/user-attachments/assets/793b09cc-4cb2-445a-93c7-f40335cf65e5" />


**Question 10**
---
-- Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

```sql
SELECT age, MIN(income) 
FROM employee 
GROUP BY age
HAVING MIN(income) < 400000;
```

**Output:**

<img width="565" height="333" alt="image" src="https://github.com/user-attachments/assets/e63e8128-b49d-45e0-b1ef-88fe41824542" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
