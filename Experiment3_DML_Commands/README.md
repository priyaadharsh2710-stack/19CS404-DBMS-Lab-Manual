# Experiment 3: DML Commands

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
---- <img width="992" height="502" alt="image" src="https://github.com/user-attachments/assets/96c7ef05-3cfc-472c-8bd5-c04069874bed" />

```sql
--
UPDATE EMPLOYEES
SET EMAIL = 'not available',
    COMMISSION_PCT = 0.55
WHERE DEPARTMENT_ID = 110;
```

**Output:**

<img width="1000" height="382" alt="image" src="https://github.com/user-attachments/assets/05c0cfdf-26cf-435c-9c70-d601ad6f06a5" />


**Question 2**
---
-- <img width="873" height="458" alt="image" src="https://github.com/user-attachments/assets/52d1f77c-44a0-49a9-80d0-be36f70c30da" />


```sql
--
UPDATE PRODUCTS
SET SELL_PRICE = SELL_PRICE + (SELL_PRICE * 10 / 100)
WHERE SUPPLIER_ID = 6;
```

**Output:**

<img width="990" height="517" alt="image" src="https://github.com/user-attachments/assets/238487b8-a562-4c63-acc1-e71abc544faf" />

**Question 3**
---
-- <img width="992" height="512" alt="image" src="https://github.com/user-attachments/assets/9322d997-af23-4a7c-aced-362f5d300d99" />

```sql
--
UPDATE purchases
SET per_unit_price = 25,
    total_price = quantity * 25
WHERE purchase_date = '2022-08-15'
  AND product_id = 12;
```

**Output:**

<img width="991" height="490" alt="image" src="https://github.com/user-attachments/assets/93d9a318-d8cd-4369-abf5-e147d34448d7" />

**Question 4**
---
-- <img width="798" height="250" alt="image" src="https://github.com/user-attachments/assets/ef980847-9d70-4210-8e2a-7d7eeb060174" />


```sql
--
UPDATE Products
SET quantity = quantity * 1.10;
```

**Output:**

<img width="990" height="575" alt="image" src="https://github.com/user-attachments/assets/96097ae0-91f0-4792-87f1-5e2ed322a6f6" />


**Question 5**
---
-- <img width="912" height="230" alt="image" src="https://github.com/user-attachments/assets/8698d750-b8e1-43f4-9676-7c323e1d3e49" />


```sql
--
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';
```

**Output:**

<img width="991" height="437" alt="image" src="https://github.com/user-attachments/assets/2c625f51-ad5a-4ca3-a0f3-1916e0afeaae" />

**Question 6**
---
-- <img width="982" height="441" alt="image" src="https://github.com/user-attachments/assets/1c34c73b-8882-470d-95b8-590b0337f7b0" />

```sql
--
DELETE FROM Doctors
WHERE last_name = 'Brown'
  AND specialization IN ('Pediatrics', 'Cardiology');
```

**Output:**

<img width="995" height="600" alt="image" src="https://github.com/user-attachments/assets/f8bac584-2cad-4d7e-aba1-db162cce3165" />


**Question 7**
---
-- <img width="993" height="481" alt="image" src="https://github.com/user-attachments/assets/81da6225-aa1f-4768-9de6-f8e5d0bb2e32" />


```sql
--
DELETE FROM customer
WHERE CUST_NAME LIKE '%Holmes%';
```

**Output:**

<img width="982" height="510" alt="image" src="https://github.com/user-attachments/assets/63029003-e4f6-4fbc-bf16-48ea4f26a36d" />

**Question 8**
---
-- <img width="986" height="436" alt="image" src="https://github.com/user-attachments/assets/c4a715f2-2859-4966-b350-ef30374aae13" />


```sql
--
DELETE FROM customer
WHERE CUST_CITY <> 'New York'
  AND OUTSTANDING_AMT > 5000;
```

**Output:**

<img width="988" height="537" alt="image" src="https://github.com/user-attachments/assets/ef1a5cf8-3a0d-4c6b-b3df-aafebce338f0" />


**Question 9**
---
-- <img width="992" height="553" alt="image" src="https://github.com/user-attachments/assets/a775bbad-abcb-4f83-a022-3ce190d92cdc" />


```sql
--
DELETE FROM customer
WHERE GRADE < 2;
```

**Output:**

<img width="700" height="448" alt="image" src="https://github.com/user-attachments/assets/bb381d41-cc93-478e-9ac4-721258d9d45f" />


**Question 10**
---
-- <img width="986" height="607" alt="image" src="https://github.com/user-attachments/assets/bbfe471c-ce12-468f-bc4a-819865979030" />


```sql
--
DELETE FROM customer
WHERE AGENT_CODE IN ('A003', 'A008');
```

**Output:**

<img width="830" height="556" alt="image" src="https://github.com/user-attachments/assets/7c165347-4644-4df6-9681-517bda346e72" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
