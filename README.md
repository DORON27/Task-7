# Task 7 - Creating Views (SQL Developer Internship)

## Objective
- Learn to create and use SQL Views  
- Understand abstraction and security using views  
- Practice with CREATE VIEW, DROP VIEW, and WITH CHECK OPTION

---

##  Tools Used
-  MySQL Workbench

---

##  Database Setup
We created two tables: *Department* and *Employees* with some sample data.

```sql
CREATE TABLE Department (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);

CREATE TABLE Employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    dept_id INT,
    salary DECIMAL(10,2),
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
);

INSERT INTO Department (dept_id, dept_name) VALUES
(1, 'HR'),
(2, 'IT'),
(3, 'Finance');

INSERT INTO Employees (emp_id, name, dept_id, salary) VALUES
(101, 'Alice', 1, 45000),
(102, 'Bob', 2, 60000),
(103, 'Charlie', 2, 75000),
(104, 'David', 3, 50000),
(105, 'Eva', 1, 55000);
```

### Creating Views
1.Basic View
```sql
create view HighSalaryEmployees
as
select name,salary
from Employees
where salary> 50000;
```

2.Join View
```sql
create view EmployeeDepartment as
select e.emp_id,e.name,d.dept_name,e.salary
from Employees e
join Department d on e.dept_id=d.dept_id;
```

3.Restricted View
```sql
create view EmployeePublic as
select name,dept_id
from Employees;
```

4.View with Check Option
```sql
create view SecureHighSalary as
select emp_id,name,salary
from Employees
where salary>50000
with check option;
```

### Using Views
```sql
select*from HighSalaryEMPLOYEES;
select*from EmployeeDepartment;
select*from EmployeePublic;
```
