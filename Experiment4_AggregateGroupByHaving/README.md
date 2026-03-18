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

How many medical records were created in each month?

```
SELECT strftime('%Y-%m',Date) AS Month,COUNT(*) AS TotalRecords
FROM MedicalRecords 
GROUP BY Month;
```

**Output:**

<img width="385" height="250" alt="image" src="https://github.com/user-attachments/assets/5ed892fe-6cf6-4a50-818f-b4ad136d1108" />


**Question 2**

What is the average dosage prescribed for each medication?

```
SELECT Medication, AVG(Dosage) AS AvgDosage
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

<img width="393" height="470" alt="image" src="https://github.com/user-attachments/assets/e28d9bf3-07b2-4957-92b4-f9c647d6f572" />


**Question 3**

How many medical records are there for each patient?

```
SELECT PatientID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

<img width="401" height="194" alt="image" src="https://github.com/user-attachments/assets/e1b520f0-e0aa-456a-b9e1-0e76733da64b" />


**Question 4**

Write a SQL query to find the youngest employee in the company?

```
SELECT name AS Employee_Name, MIN(age) AS Age
FROM employee;
```

**Output:**

<img width="409" height="190" alt="image" src="https://github.com/user-attachments/assets/6550c231-ca28-4272-81e4-aae0282b2292" />


**Question 5**

Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

```
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city="Noida";
```

**Output:**

<img width="221" height="185" alt="image" src="https://github.com/user-attachments/assets/726c7b2e-c461-4f62-b452-a887ec567de5" />


**Question 6**

Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city

```
SELECT AVG(LENGTH(email)) AS avg_email_length_below_30
FROM customer
WHERE city ="Mumbai";
```

**Output:**

<img width="410" height="193" alt="image" src="https://github.com/user-attachments/assets/02fad555-0533-4cf6-aae7-e21b55b2b768" />


**Question 7**

Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

```
SELECT COUNT(*) AS COUNT
FROM(
SELECT DISTINCT age
FROM employee
);
```

**Output:**

<img width="220" height="194" alt="image" src="https://github.com/user-attachments/assets/ed5a04bb-084c-4fb3-ad59-d98348088425" />


**Question 8**

Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and
includes only those age groups where the minimum income is less than 400,000

```
SELECT age,
       MIN(income) 
FROM employee
GROUP BY age
HAVING MIN(income)<400000;
```

**Output:**

<img width="378" height="214" alt="image" src="https://github.com/user-attachments/assets/e0044817-be86-4b12-ab75-ef4e4cb0f445" />


**Question 9**

Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

```
SELECT AVG( purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="322" height="268" alt="image" src="https://github.com/user-attachments/assets/98ee3175-7d66-4699-aee4-8e1a65377bb6" />


**Question 10**

Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and
includes only those age groups where the maximum income is greater than 2,000,000.

```
SELECT age,
       MAX(income)
FROM employee
GROUP BY age
HAVING MAX(income)>2000000;
```

**Output:**

<img width="375" height="218" alt="image" src="https://github.com/user-attachments/assets/fd59577a-5b14-4653-991b-f4454fb6e260" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
