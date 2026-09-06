# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
-- <img width="922" height="413" alt="image" src="https://github.com/user-attachments/assets/3594a77e-4850-47a7-89d3-63792e92fad8" />


```sql
-- 
SELECT medication_id AS medic, medication_name, dosage
FROM Medications
WHERE CAST(REPLACE(dosage, 'mg', '') AS INTEGER) = (
    SELECT MAX(CAST(REPLACE(dosage, 'mg', '') AS INTEGER))
    FROM Medications
);
```

**Output:**

<img width="776" height="382" alt="image" src="https://github.com/user-attachments/assets/e4561ff7-f241-4ea6-8529-cad5cd9fe563" />


**Question 2**
---
--<img width="790" height="593" alt="image" src="https://github.com/user-attachments/assets/00e8aa41-2707-420f-a23f-753351b8e99b" />


```sql
--
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;
```

**Output:**

<img width="1023" height="487" alt="image" src="https://github.com/user-attachments/assets/abc57318-3bf7-402f-aaeb-61b505fa96d6" />

**Question 3**
---
-- <img width="960" height="492" alt="image" src="https://github.com/user-attachments/assets/5362097a-8186-4f46-82d0-3c1d50673649" />

```sql
-- 
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);
```

**Output:**

<img width="1026" height="355" alt="image" src="https://github.com/user-attachments/assets/86178522-01e3-4515-bfb4-7455614e22eb" />

**Question 4**
---
--<img width="991" height="491" alt="image" src="https://github.com/user-attachments/assets/bb58fd57-e46f-499e-90fb-73feae24d219" />


```sql
-- 
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM ORDERS
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM ORDERS
    WHERE ord_date = '2012-10-10'
);
```

**Output:**

<img width="1025" height="372" alt="image" src="https://github.com/user-attachments/assets/a690f671-d473-48ed-96fd-7f09bb640df4" />


**Question 5**
---
-- <img width="972" height="597" alt="image" src="https://github.com/user-attachments/assets/29617085-6f8d-4af5-a457-7bfd4f84d86f" />


```sql
-- 
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.city = 'London';
```

**Output:**

<img width="1016" height="342" alt="image" src="https://github.com/user-attachments/assets/8b03c260-5dfe-47c2-868d-3c69e24809a3" />

**Question 6**
---
-- <img width="913" height="452" alt="image" src="https://github.com/user-attachments/assets/1a604a2c-e695-4f6b-81b9-3028a2ffa30a" />


```sql
-- 
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);
```

**Output:**

<img width="635" height="432" alt="image" src="https://github.com/user-attachments/assets/2f976a50-22d8-46bf-8f42-3d33bc48496a" />


**Question 7**
---
-- <img width="1010" height="617" alt="Screenshot 2026-09-06 104201" src="https://github.com/user-attachments/assets/6c1f3289-56ee-4d34-a0c6-70201ccf479e" />


```sql
-- 
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);
```

**Output:**

<img width="862" height="392" alt="image" src="https://github.com/user-attachments/assets/287c25c1-7ab2-4a6c-9692-a832f0189b6d" />

**Question 8**
---
--<img width="901" height="535" alt="image" src="https://github.com/user-attachments/assets/8622be17-c9d9-432c-992a-0ac09366f4b4" />


```sql
-- 
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);
```

**Output:**

<img width="1022" height="437" alt="image" src="https://github.com/user-attachments/assets/5b009721-9572-46f6-b6fb-41dc48eef346" />


**Question 9**
---
-- <img width="922" height="413" alt="image" src="https://github.com/user-attachments/assets/8627de20-b3a6-4819-a111-6d134f9de173" />


```sql
-- 
SELECT medication_id AS medic, medication_name, dosage
FROM Medications
WHERE CAST(REPLACE(dosage, 'mg', '') AS INTEGER) = (
    SELECT MAX(CAST(REPLACE(dosage, 'mg', '') AS INTEGER))
    FROM Medications
);

```

**Output:**

<img width="776" height="382" alt="image" src="https://github.com/user-attachments/assets/2c2060ad-1527-4327-b369-a26511978461" />


**Question 10**
---
-- <img width="996" height="498" alt="image" src="https://github.com/user-attachments/assets/b65ced0a-b8ef-40d1-b3c3-640ed0c411f9" />


```sql
-- 
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);
```

**Output:**

<img width="1022" height="382" alt="image" src="https://github.com/user-attachments/assets/6b123394-19f9-44b9-aaa0-25ffd8c636d3" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
