## SQL Real-World Scenarios and Solutions
---
### Scenario 1: Employee Salary Filtering

A company wants to find all employees with a salary greater than 50,000. Write an SQL query to retrieve the required employee records.

**Table Name:** `employees`

## Table Structure: 'employees'

<img width="879" height="45" alt="image" src="https://github.com/user-attachments/assets/4fd795ec-f169-4b6b-b74f-1d2d0f2741af" />


### SQL Query

SELECT *
    FROM employees	
    WHERE salary > 50000;

### 📊 Query Output

<img width="961" height="293" alt="image" src="https://github.com/user-attachments/assets/ababc831-0744-497a-8263-c6fbf77ac36d" />

###  Query Logic

The **WHERE** clause filters rows based on a condition. Only employees with salary greater than 50,000 are returned. Rows with salary equalto or less than 50,000 are excluded.


