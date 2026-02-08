# sql_views
create views using joins,group by,aggregare functions
#=================views
use mall;
select*from emp;
CREATE TABLE dept (
    DeptID INT PRIMARY KEY,
    Department VARCHAR(50),
    Manager VARCHAR(50)
);
INSERT INTO dept (DeptID, Department, Manager) VALUES
(101, 'HR', 'Ramesh'),
(102, 'Finance', 'Suresh'),
(103, 'IT', 'Mahesh'),
(104, 'Sales', 'Naresh');
SELECT * FROM dept;
select*from emp;

-- Employee Details with Department Manager (JOIN View)
create view emp_department_details as
SELECT e.EmpID, e.Name, e.Department, d.Manager from emp e inner join dept d on e.department=d.department;
select*from emp_department_details;

-- Department-wise Total Salary (GROUP BY + SUM)
CREATE VIEW deptt_total_salary AS
SELECT Department, SUM(Salary) AS total_salary FROM emp GROUP BY Department;
SELECT * FROM deptt_total_salary;

-- Department-wise Average Salary (AVG)
CREATE VIEW dept_avg_salary AS
SELECT Department, AVG(Salary) AS avg_salary FROM emp GROUP BY Department;
SELECT * FROM dept_avg_salary;

-- Count Employees in Each City (COUNT)
CREATE VIEW city_employee_count AS
SELECT City, COUNT(*) AS total_employees FROM emp GROUP BY City;
select*from city_employee_count;

DROP VIEW dept_avg_salary;
