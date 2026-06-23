## SQL Real-World Scenarios and Solutions
---
### Scenario 1: Employee Salary Filtering

A company wants to find all employees with a salary greater than 50,000. Write an SQL query to retrieve the required employee records.

## Table Structure: 'employees'

| Column        | Data Type          |
|---------------|--------------------|
| employee_id   | INTEGER (PK)       |
| first_name    | VARCHAR(50)        |
| last_name     | VARCHAR(50)        |
| department_id | INTEGER            |
| salary        | NUMERIC(10,2)      |
| hire_date     | DATE               |
| manager_id    | INTEGER            |

### SQL Query

SELECT *
    FROM employees	
    WHERE salary > 50000;

### 📊 Query Output

<img width="961" height="293" alt="image" src="https://github.com/user-attachments/assets/ababc831-0744-497a-8263-c6fbf77ac36d" />

###  Query Logic

The WHERE clause filters rows based on a condition. Only employeeswith salary greater than 50,000 are returned. Rows with salary equal
to or less than 50,000 are excluded.


