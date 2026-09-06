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
-- <img width="897" height="392" alt="image" src="https://github.com/user-attachments/assets/ec399fed-ad64-460e-b34f-c31118e71596" />


```sql
-- 
SELECT Address, COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Address;
```

**Output:**

<img width="608" height="327" alt="image" src="https://github.com/user-attachments/assets/36990327-db39-49bd-940d-4dcc4257442d" />


**Question 2**
---
--<img width="793" height="538" alt="image" src="https://github.com/user-attachments/assets/50d26d3a-2dc0-42ae-818b-01ae083374ed" />


```sql
-- 
SELECT
    InsuranceCompany,
    AVG(CAST(strftime('%Y', EndDate) AS INTEGER) -
        CAST(strftime('%Y', StartDate) AS INTEGER)) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany
ORDER BY InsuranceCompany;
```

**Output:**

<img width="803" height="545" alt="image" src="https://github.com/user-attachments/assets/96f58910-06cd-45b3-bc93-f990fd09a5a2" />


**Question 3**
---
-- <img width="912" height="517" alt="image" src="https://github.com/user-attachments/assets/dc9e6d67-f8e1-498e-b220-a3ecebfa47e4" />


```sql
-- SELECT
    Medication,
    COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication
ORDER BY Medication;
```

**Output:**

<img width="791" height="598" alt="image" src="https://github.com/user-attachments/assets/7908db04-7b0f-4db7-97e1-16df9a8acab3" />

**Question 4**
---
-- <img width="825" height="425" alt="image" src="https://github.com/user-attachments/assets/af23adf0-1192-4cf3-9baf-3b2e00067822" />


```sql
--
 SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="557" height="310" alt="image" src="https://github.com/user-attachments/assets/1f2639d4-702e-4c58-abca-f5e7bbcf68e0" />

**Question 5**
---
-- <img width="562" height="405" alt="image" src="https://github.com/user-attachments/assets/6781f2ab-7156-4d51-8d19-e2ffe8028130" />


```sql
--
SELECT MAX(purch_amt) AS MAXIMUM
FROM orders;
```

**Output:**

<img width="455" height="308" alt="image" src="https://github.com/user-attachments/assets/5cdec232-da8f-47eb-bfc0-00c826f953bf" />


**Question 6**
---
--<img width="791" height="386" alt="image" src="https://github.com/user-attachments/assets/c7a3c426-228b-4ba7-9b5b-c7b839fc22f0" />


```sql
-- 
SELECT SUM(purch_amt) AS TOTAL
FROM orders;
```

**Output:**

<img width="575" height="311" alt="image" src="https://github.com/user-attachments/assets/fc8c44d2-7010-4255-aae8-052b8f56f62c" />


**Question 7**
---
-- <img width="617" height="417" alt="image" src="https://github.com/user-attachments/assets/6bdc7c3b-d946-4608-8d8f-a5b66c0ebff4" />


```sql
--
SELECT name AS Employee_Name, age AS Age
FROM employee
ORDER BY age ASC
LIMIT 1;
```

**Output:**

<img width="657" height="305" alt="image" src="https://github.com/user-attachments/assets/4e2ea17d-423c-486e-bdf2-4ba17d9e2808" />


**Question 8**
---
-- <img width="946" height="410" alt="image" src="https://github.com/user-attachments/assets/fbc4edf1-cfad-475d-875e-da184b46aa81" />


```sql
--
SELECT jdate, MAX(workhour) AS "MAX(workhour)"
FROM employee1
GROUP BY jdate
HAVING MAX(workhour) > 12;
```

**Output:**

<img width="670" height="366" alt="image" src="https://github.com/user-attachments/assets/b26e1b5e-7a70-4af4-b03d-1ccaeab5fbfc" />


**Question 9**
---
-- <img width="722" height="453" alt="image" src="https://github.com/user-attachments/assets/14574dd0-e968-4e5d-ac75-e356fa8a084a" />



```sql
--
SELECT address, AVG(salary) AS "AVG(salary)"
FROM customer1
GROUP BY address
HAVING AVG(salary) < 15000;
```

**Output:**

<img width="702" height="493" alt="image" src="https://github.com/user-attachments/assets/93c572fb-ce54-4f4d-a01f-2f84c8ebe575" />

**Question 10**
---
-- <img width="977" height="417" alt="image" src="https://github.com/user-attachments/assets/c20c74ec-4379-42c2-9228-04c08db5a6b9" />


```sql
-- 
SELECT category_id, product_name, MAX(price) AS Price
FROM products
GROUP BY category_id
HAVING MAX(price) > 15;
```

**Output:**

<img width="757" height="367" alt="image" src="https://github.com/user-attachments/assets/d5e2e082-9ae3-4294-8fba-54e86881ac21" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
