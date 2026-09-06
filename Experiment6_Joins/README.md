<img width="1000" height="623" alt="image" src="https://github.com/user-attachments/assets/ca46e922-2b76-44de-aa37-e7c7a0fed440" /># Experiment 6: Joins

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
-- <img width="1058" height="620" alt="image" src="https://github.com/user-attachments/assets/2fecd90c-22f0-49c6-8732-38d31bbc0b28" />


```sql
-- 
SELECT p.first_name
FROM patients p
INNER JOIN surgeries s
    ON p.patient_id = s.patient_id
WHERE s.surgery_date = '2024-01-15';
```

**Output:**
<img width="442" height="326" alt="image" src="https://github.com/user-attachments/assets/a99411c5-90ab-48a9-aed3-29032d24b50c" />


**Question 2**
---
-- <img width="968" height="612" alt="image" src="https://github.com/user-attachments/assets/0785c5c6-aac7-4132-a054-648604fbcbf7" />


```sql
-- 
SELECT a.cust_name,
       a.city,
       b.ord_no,
       b.ord_date,
       b.purch_amt AS "Order Amount",
       c.name,
       c.commission
FROM customer a
LEFT OUTER JOIN orders b
    ON a.customer_id = b.customer_id
LEFT OUTER JOIN salesman c
    ON c.salesman_id = b.salesman_id;
```

**Output:**

<img width="1023" height="597" alt="image" src="https://github.com/user-attachments/assets/968a269f-f262-4181-8f4a-fa345677185d" />


**Question 3**
---
-- <img width="1000" height="623" alt="image" src="https://github.com/user-attachments/assets/756bcb54-e026-44b4-9c7a-1f4e02db9ece" />


```sql
-- 
SELECT o.ord_no,
       o.purch_amt,
       o.ord_date,
       c.cust_name,
       c.city AS customer_city,
       c.grade,
       s.name AS salesman_name,
       s.city AS salesman_city,
       s.commission
FROM orders o
INNER JOIN customer c
    ON o.customer_id = c.customer_id
INNER JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1027" height="617" alt="image" src="https://github.com/user-attachments/assets/6632df1e-e597-4871-874d-1a0bed2c6e10" />


**Question 4**
---
-- <img width="1010" height="567" alt="image" src="https://github.com/user-attachments/assets/838e377e-0444-4014-81f4-74656c2d8de9" />


```sql
-- 
SELECT p.*
FROM patients p
INNER JOIN test_results tr
    ON p.patient_id = tr.patient_id
WHERE tr.test_name IN ('Blood Test', 'Blood Pressure')
  AND tr.result NOT LIKE '%Normal%';
```

**Output:**

<img width="1020" height="395" alt="image" src="https://github.com/user-attachments/assets/e301ba14-557e-4580-aa41-b446aecd54cd" />

**Question 5**
---
-- <img width="983" height="623" alt="image" src="https://github.com/user-attachments/assets/3f5979fc-65df-40a9-9b96-ad22d1c6d023" />


```sql
--
SELECT p.*, d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d
    ON p.doctor_id = d.doctor_id;
```

**Output:**

<img width="1018" height="468" alt="image" src="https://github.com/user-attachments/assets/01775882-0907-421f-851d-0df1b3112725" />


**Question 6**
---
-- <img width="1002" height="607" alt="image" src="https://github.com/user-attachments/assets/6b99fa93-7cc2-4d0a-88da-bc12911e4615" />

```sql
-- 
SELECT a.cust_name,
       a.city,
       b.ord_no,
       b.ord_date,
       b.purch_amt AS "Order Amount"
FROM customer a
LEFT OUTER JOIN orders b
ON a.customer_id = b.customer_id
ORDER BY b.ord_date ASC;
```

**Output:**
<img width="1007" height="622" alt="image" src="https://github.com/user-attachments/assets/a1a1914c-c5bf-4547-ab0a-bd1590132d3e" />

**Question 7**
---
--<img width="976" height="503" alt="image" src="https://github.com/user-attachments/assets/fe23a471-8db2-4771-8064-8e0c4549093e" />


```sql
--
SELECT c.cust_name AS "Customer Name",
       c.city,
       s.name AS "Salesman",
       s.commission
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

<img width="1017" height="576" alt="image" src="https://github.com/user-attachments/assets/f809cb81-ae12-4374-aff8-761f1da14a76" />


**Question 8**
---
--<img width="1021" height="417" alt="image" src="https://github.com/user-attachments/assets/f01b3369-0d38-4d9d-a962-7bb271fe1d6e" />


```sql
-- 
SELECT c.cust_name, s.commission
FROM customer c
LEFT JOIN salesman s
ON c.salesman_id = s.salesman_id;
```

**Output:**
<img width="625" height="473" alt="image" src="https://github.com/user-attachments/assets/d071dca8-d5a0-4218-a399-dbd88a897558" />


**Question 9**
---
-- <img width="990" height="606" alt="image" src="https://github.com/user-attachments/assets/4b495731-c289-4a1b-8b44-a14739bbef73" />


```sql
-- 
SELECT o.ord_no,
       o.ord_date,
       o.purch_amt,
       c.cust_name AS "Customer Name",
       c.grade,
       s.name AS "Salesman",
       s.commission
FROM orders o
INNER JOIN customer c
    ON o.customer_id = c.customer_id
INNER JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1006" height="595" alt="image" src="https://github.com/user-attachments/assets/787981ca-68fa-4885-960b-f2e861de2813" />

**Question 10**
---
-- <img width="1007" height="425" alt="image" src="https://github.com/user-attachments/assets/7417b0a4-516a-475b-8479-362c0f274805" />


```sql
-- 
SELECT c.cust_name,
       o.ord_no,
       o.ord_date,
       o.purch_amt
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.purch_amt > 1000;
```

**Output:**

<img width="1016" height="511" alt="image" src="https://github.com/user-attachments/assets/1d72d3ac-7b95-4598-a31e-a05bf7751d04" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
