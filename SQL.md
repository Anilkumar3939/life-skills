
# SQL Technical Report: Basics, Joins, and Aggregations

## Abstract
Structured Query Language (SQL) is the foundation of relational database management. It is used for storing, manipulating, and retrieving data in databases. This technical report covers SQL basics, join operations, and aggregation functions with practical code examples to aid in comprehension.

---

## 1. Introduction
SQL is an ANSI (American National Standards Institute) standard language, but there are many different versions of the SQL language. However, to be compliant with the ANSI standard, all SQL versions must support the major commands such as SELECT, UPDATE, DELETE, INSERT, WHERE, etc.

SQL is used to perform tasks such as updating data on a database or retrieving data from a database. Some common relational database management systems that use SQL are MySQL, PostgreSQL, SQL Server, and SQLite.

---

## 2. SQL Basics

### 2.1 Creating Tables
Tables are the basic unit of storage in SQL. Each table contains rows and columns.
```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT,
    Salary DECIMAL(10, 2),
    DepartmentID INT
);
```

### 2.2 Inserting Data
You can insert rows into a table using the `INSERT` command.
```sql
INSERT INTO Employees (EmployeeID, Name, Age, Salary, DepartmentID)
VALUES (1, 'John Doe', 30, 50000.00, 101);
```

### 2.3 Querying Data
Retrieve data from tables using the `SELECT` statement.
```sql
SELECT * FROM Employees;
SELECT Name, Salary FROM Employees WHERE Salary > 40000;
```

### 2.4 Updating Records
Update existing records using the `UPDATE` statement.
```sql
UPDATE Employees SET Salary = 55000 WHERE EmployeeID = 1;
```

### 2.5 Deleting Records
Remove records with the `DELETE` statement.
```sql
DELETE FROM Employees WHERE EmployeeID = 1;
```

---

## 3. SQL Joins

### 3.1 What is a Join?
A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

### 3.2 Example Tables

**Employees Table:**

| EmployeeID | Name     | DepartmentID |
|------------|----------|--------------|
| 1          | John     | 101          |
| 2          | Alice    | 102          |

**Departments Table:**

| DepartmentID | Name       |
|--------------|------------|
| 101          | HR         |
| 102          | IT         |

### 3.3 INNER JOIN
Returns records that have matching values in both tables.
```sql
SELECT Employees.Name, Departments.Name AS Department
FROM Employees
INNER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
```

### 3.4 LEFT JOIN
Returns all records from the left table and matched records from the right table.
```sql
SELECT Employees.Name, Departments.Name AS Department
FROM Employees
LEFT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
```

### 3.5 RIGHT JOIN
Returns all records from the right table and matched records from the left table.
```sql
SELECT Employees.Name, Departments.Name AS Department
FROM Employees
RIGHT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
```

### 3.6 FULL OUTER JOIN
Returns all records when there is a match in either left or right table.
```sql
SELECT Employees.Name, Departments.Name AS Department
FROM Employees
FULL OUTER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
```

---

## 4. Aggregations

SQL aggregation functions are used to perform a calculation on a set of values and return a single value.

### 4.1 COUNT
Counts the number of rows.
```sql
SELECT COUNT(*) AS TotalEmployees FROM Employees;
```

### 4.2 SUM
Calculates the total sum of a numeric column.
```sql
SELECT SUM(Salary) AS TotalSalaries FROM Employees;
```

### 4.3 AVG
Returns the average value of a numeric column.
```sql
SELECT AVG(Salary) AS AverageSalary FROM Employees;
```

### 4.4 MAX and MIN
Returns the maximum and minimum value of a column.
```sql
SELECT MAX(Salary) AS HighestSalary, MIN(Salary) AS LowestSalary FROM Employees;
```

### 4.5 GROUP BY
Groups rows that have the same values into summary rows.
```sql
SELECT DepartmentID, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY DepartmentID;
```

### 4.6 HAVING
Used to filter groups based on a condition.
```sql
SELECT DepartmentID, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY DepartmentID
HAVING COUNT(*) > 1;
```

---

## 5. Conclusion
SQL is an indispensable tool in the realm of databases. Whether it’s basic CRUD operations or complex aggregations and joins, SQL provides the means to efficiently interact with relational data. A solid understanding of SQL commands and their applications can significantly improve one's ability to manage and analyze data.

---

## References
- [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [MySQL Reference Manual](https://dev.mysql.com/doc/)
