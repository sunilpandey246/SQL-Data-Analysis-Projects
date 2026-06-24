## SQL Real-World Scenarios and Solutions
---
### Scenario 1: Employee Salary Filtering

A company wants to find all employees with a salary greater than 50,000. Write an SQL query to retrieve the required employee records.

### Table Structure: `employees`

| employee_id | first_name | last_name | department_id | salary | hire_date | manager_id |
|-------------|------------|-----------|---------------|--------|-----------|------------|
| INTEGER (PK)| VARCHAR(50)| VARCHAR(50)| INTEGER      | NUMERIC(10,2) | DATE | INTEGER |

### SQL Query

```sql
SELECT *
FROM employees
WHERE salary > 50000;
```

### 📊 Query Output

<img width="961" height="293" alt="image" src="https://github.com/user-attachments/assets/ababc831-0744-497a-8263-c6fbf77ac36d" />

###  Query Logic

The **WHERE** clause filters rows based on a condition. Only employees with salary greater than 50,000 are returned. Rows with salary equal to or less than 50,000 are excluded.

---
### Scenario 2: Finding Duplicate Email Addresses

A customer table contains duplicate email addresses. Write an SQL query to identify all duplicate emails.

### Table Structure: `customers`

| Column          | customer_id  | customer_name   | email           | phone           | status          | register_date |
|-----------------|--------------|-----------------|-----------------|-----------------|-----------------|---------------|
| Data Type       | INTEGER (PK) | VARCHAR(100)    | VARCHAR(150)    | VARCHAR(15)     | VARCHAR(20)     | DATE          |

### SQL Query

```sql
SELECT email, COUNT(*) AS count
FROM customers
GROUP BY email
HAVING COUNT(*) > 1;
```

### Query Output

<img width="973" height="288" alt="image" src="https://github.com/user-attachments/assets/3809b13b-4105-459d-9562-7b31dd49c779" />


### Query Logic

The GROUP BY clause groups all rows by email address. 

The COUNT(*) counts how many times each email appears. 

The HAVING clause filters and returns only those emails 

where the count is greater than 1, indicating duplicates.

---

## Scenario 3: Correcting Wrong Data

A data entry error was made in the employees table — the salary for employee_id 5 was entered as 30,000 instead of 60,000. Write a query to fix this.

## Table Structure: `employees`

| Column    | employee_id  | first_name  | last_name   | department_id | salary        | hire_date | manager_id |
|-----------|--------------|-------------|-------------|---------------|---------------|-----------|------------|
| Data Type | INTEGER (PK) | VARCHAR(50) | VARCHAR(50) | INTEGER       | NUMERIC(10,2) | DATE      | INTEGER    |

## SQL Query

```sql
UPDATE employees
SET salary = 60000
WHERE employee_id = 5;
```

## Query Output

<img width="932" height="109" alt="image" src="https://github.com/user-attachments/assets/4a2a328d-9f54-47a8-9003-5a645686f87f" />


## Query Logic

The UPDATE statement modifies existing records in a table.

The SET clause specifies the column and its new correct value.

The WHERE clause ensures only the targeted row is updated.

Without WHERE, all rows in the table would be updated.

---

## Scenario 4: Finding NULL Phone Numbers

A customers table contains NULL values in the phone number column. How would you retrieve only rows with missing phone numbers?

## Table Structure: `customers`

| Column    | customer_id  | customer_name | email        | phone       | status      | register_date |
|-----------|--------------|---------------|--------------|-------------|-------------|---------------|
| Data Type | INTEGER (PK) | VARCHAR(100)  | VARCHAR(150) | VARCHAR(15) | VARCHAR(20) | DATE          |

## SQL Query

```sql
SELECT *
FROM customers
WHERE phone IS NULL;
```

## Query Output

<img width="981" height="255" alt="image" src="https://github.com/user-attachments/assets/080b3c1b-e820-4e4e-96da-798e3c30165e" />


## Query Logic

The IS NULL condition checks for missing or empty values in a column.

Only rows where the phone column has no value are returned.

IS NULL is different from = NULL — in SQL, NULL cannot be 
compared using = operator, IS NULL is the correct syntax.

---

## Scenario 5: Sorting Employees by Highest Salary

You want to display employees sorted by highest salary first. Which clause would you use?

## Table Structure: `employees`

| Column    | employee_id  | first_name  | last_name   | department_id | salary        | hire_date | manager_id |
|-----------|--------------|-------------|-------------|---------------|---------------|-----------|------------|
| Data Type | INTEGER (PK) | VARCHAR(50) | VARCHAR(50) | INTEGER       | NUMERIC(10,2) | DATE      | INTEGER    |

## SQL Query

```sql
SELECT *
FROM employees
ORDER BY salary DESC;
```

## Query Output

<img width="968" height="269" alt="image" src="https://github.com/user-attachments/assets/2eac9000-5f99-4ca5-90bf-5497e50ead54" />

## Query Logic

The ORDER BY clause sorts the result set based on a specified column.

DESC (Descending) arranges values from highest to lowest.

ASC (Ascending) is the default — it sorts from lowest to highest.

Without ORDER BY, SQL does not guarantee any specific order of results.

---

## Scenario 6: Retrieving Customers with Their Orders

Two tables contain customer and order information. How would 
you retrieve customers along with their orders?

## Table Structure: `customers`

| Column    | customer_id  | customer_name | email        | phone       | status      | register_date |
|-----------|--------------|---------------|--------------|-------------|-------------|---------------|
| Data Type | INTEGER (PK) | VARCHAR(100)  | VARCHAR(150) | VARCHAR(15) | VARCHAR(20) | DATE          |

## Table Structure: `orders`

| Column    | order_id     | customer_id | order_date | total_amount  | product_id |
|-----------|--------------|-------------|------------|---------------|------------|
| Data Type | INTEGER (PK) | INTEGER     | DATE       | NUMERIC(10,2) | INTEGER    |

## SQL Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id, o.order_date
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

## Query Output

<img width="899" height="292" alt="image" src="https://github.com/user-attachments/assets/e5358325-28a4-4c25-87bf-ad0cb035bec8" />


## Query Logic

INNER JOIN combines rows from two tables based on a matching condition.

The ON clause defines the join condition — here customer_id 
is the common column between both tables.

Only customers who have placed at least one order are returned.

Customers with no orders are excluded from the result.

---
## Scenario 7: Finding Customers Without Orders

You need to find customers who have not placed any orders. Which join would you use?

## Table Structure: `customers`

| Column    | customer_id  | customer_name | email        | phone       | status      | register_date |
|-----------|--------------|---------------|--------------|-------------|-------------|---------------|
| Data Type | INTEGER (PK) | VARCHAR(100)  | VARCHAR(150) | VARCHAR(15) | VARCHAR(20) | DATE          |

## Table Structure: `orders`

| Column    | order_id     | customer_id | order_date | total_amount  | product_id |
|-----------|--------------|-------------|------------|---------------|------------|
| Data Type | INTEGER (PK) | INTEGER     | DATE       | NUMERIC(10,2) | INTEGER    |

## SQL Query

```sql
SELECT c.customer_id, c.customer_name
    FROM customers c
    LEFT JOIN orders o
    ON c.customer_id = o.customer_id
    WHERE o.order_id IS NULL;
```

## Query Output

<img width="985" height="151" alt="image" src="https://github.com/user-attachments/assets/d73e3003-b2a7-44d8-9cc0-bd87d3c1a562" />

## Query Logic

LEFT JOIN keeps all customers from the customers table.

It tries to find matching orders using customer_id.

Customers without orders get NULL values in the orders table columns.

WHERE o.order_id IS NULL filters only customers who have not placed any orders.

The result shows customers with no order history.

---

## Scenario 8: Calculating Total Sales by Employee

A manager asks for the total sales made by each employee. Which SQL function and clause would help?

## Table Structure: `sales`

| sale_id | employee_id | sale_date | sales_amount |
|----------|------------|------------|-------------|
| INTEGER (PK) | INTEGER | DATE | NUMERIC(10,2) |

## SQL Query

```sql
SELECT employee_id,
       SUM(sales_amount) AS total_sales
FROM sales
GROUP BY employee_id;
```

## 📊 Query Output

<img width="746" height="271" alt="image" src="https://github.com/user-attachments/assets/7cfe8618-73d9-45dd-a424-42d9b0620979" />

## Query Logic

The **SUM()** function calculates the total sales amount for each employee. The **GROUP BY** clause groups records based on `employee_id`, allowing SQL to calculate the total sales separately for each employee. The result contains one row per employee along with their total sales amount.

---

## Scenario 9: Counting Employees in Each Department

You want to count how many employees work in each department. How would you do it?

## Table Structure: `employees`

| employee_id | first_name | last_name | department_id | salary | hire_date | manager_id |
|-------------|------------|-----------|---------------|--------|-----------|------------|
| INTEGER (PK) | VARCHAR(50) | VARCHAR(50) | INTEGER | NUMERIC(10,2) | DATE | INTEGER |

## SQL Query

```sql
SELECT department_id,
       COUNT(*) AS employee_count
FROM employees
GROUP BY department_id;
```

## 📊 Query Output

<img width="825" height="286" alt="image" src="https://github.com/user-attachments/assets/71a86adc-d3bc-455f-a358-d3117b6d7fc4" />

## Query Logic

The **COUNT()** function counts the number of employees in each department. The **GROUP BY** clause groups records based on `department_id`, allowing SQL to calculate the employee count separately for each department. The result contains one row per department along with the total number of employees working in that department.

---

## Scenario 10: Finding Departments with More Than 3 Employees

A report should show only departments with more than 3 employees. Which clause would you use after GROUP BY?

### Table Structure: `employees`

| employee_id | first_name | last_name | department_id | salary | hire_date | manager_id |
|-------------|------------|-----------|---------------|--------|-----------|------------|
| INTEGER (PK) | VARCHAR(50) | VARCHAR(50) | INTEGER | NUMERIC(10,2) | DATE | INTEGER |

### SQL Query

```sql
SELECT department_id,
       COUNT(*) AS employee_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 3;
```

### 📊 Query Output

<img width="999" height="200" alt="image" src="https://github.com/user-attachments/assets/b0f106bd-7445-42d5-912a-d72062bcf4de" />


### Query Logic

The **GROUP BY** clause groups employees based on `department_id`. The **COUNT()** function calculates the number of employees in each department. The **HAVING** clause filters the grouped results and returns only those departments where the employee count is greater than 3.

---

## Scenario 11: Retrieving the First 5 Records from a Table

You need to fetch only the first 5 records from an `orders` table. How would you do it?

### Table Structure: `orders`

| order_id | customer_id | order_date | total_amount | product_id |
|-----------|------------|------------|-------------|------------|
| INTEGER (PK) | INTEGER | DATE | NUMERIC(10,2) | INTEGER |

### SQL Query

```sql
SELECT *
FROM orders
LIMIT 5;
```

### 📊 Query Output

<img width="916" height="252" alt="image" src="https://github.com/user-attachments/assets/a96d4bf8-0cff-4e21-915c-97f6697d4bd1" />


### Query Logic

The **LIMIT** clause restricts the number of rows returned by the query. `LIMIT 5` tells SQL to retrieve only the first 5 records from the `orders` table. This is commonly used to preview data, test queries, or work with large datasets without retrieving all records.

---

## Scenario 12: Updating an Employee's Department

An employee's department changed. How would you update only that employee's department?

### Table Structure: `employees`

| employee_id | first_name | last_name | department_id | salary | hire_date | manager_id |
|-------------|------------|-----------|---------------|--------|-----------|------------|
| INTEGER (PK) | VARCHAR(50) | VARCHAR(50) | INTEGER | NUMERIC(10,2) | DATE | INTEGER |

### SQL Query

```sql
UPDATE employees
SET department_id = 5
WHERE employee_id = 101;
```

### 📊 Query Output

<img width="973" height="115" alt="image" src="https://github.com/user-attachments/assets/8d2bbda7-f2a3-4315-99a3-403faf51b629" />


### Query Logic

The **UPDATE** statement modifies existing records in a table. The **SET** clause assigns a new value to the `department_id` column. The **WHERE** clause ensures that only the employee with `employee_id = 101` is updated. Without the `WHERE` clause, all employees would be assigned to department 5.

---

<img width="1077" height="510" alt="image" src="https://github.com/user-attachments/assets/0e6d63fd-6e10-4836-8916-b3fddb372d36" />


---

<img width="1073" height="514" alt="image" src="https://github.com/user-attachments/assets/840751e9-52df-42a4-86b4-e87b3d61b827" />

---

<img width="1087" height="501" alt="image" src="https://github.com/user-attachments/assets/b83855d7-3a91-4057-95d5-0a187de630ce" />

---

<img width="1065" height="517" alt="image" src="https://github.com/user-attachments/assets/0f23a646-5e18-41ba-9129-d28835899ff4" />

---




## 👤 Author: Sunil Pandey  
## 📧 Contact: sunilpandey2468@gmail.com

---







