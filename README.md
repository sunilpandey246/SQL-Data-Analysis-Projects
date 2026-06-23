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

