1.SELECT
  REGEXP_REPLACE('tf56sd#%OqH', '[^A-Z]', '') AS UppercaseLetters,
  REGEXP_REPLACE('tf56sd#%OqH', '[^a-z]', '') AS LowercaseLetters,
  REGEXP_REPLACE('tf56sd#%OqH', '[^0-9]', '') AS Numbers,
  REGEXP_REPLACE('tf56sd#%OqH', '[A-Za-z0-9]', '') AS OtherCharacters;
2.SELECT
  SPLIT_PART(FullName, ' ', 1) AS FirstName,
  SPLIT_PART(FullName, ' ', 2) AS MiddleName,
  SPLIT_PART(FullName, ' ', 3) AS LastName
FROM Students;

3.SELECT *
FROM Orders o1
WHERE o1.State = 'Texas'
  AND EXISTS (
    SELECT 1
    FROM Orders o2
    WHERE o2.CustomerID = o1.CustomerID AND o2.State = 'California'
  );

4.-- PostgreSQL example using generate_series
SELECT ProductName
FROM Products p,
     generate_series(1, p.Quantity) AS unit;

5.-- MySQL
SELECT GROUP_CONCAT(ValueColumn) AS ConcatenatedValues
FROM DMLTable;

-- PostgreSQL
SELECT STRING_AGG(ValueColumn, ',') AS ConcatenatedValues
FROM DMLTable;

6.SELECT EmployeeID, EmployeeName, HIRE_DATE,
  CASE
    WHEN AGE(NOW(), HIRE_DATE) < INTERVAL '1 year' THEN 'New Hire'
    WHEN AGE(NOW(), HIRE_DATE) < INTERVAL '5 years' THEN 'Junior'
    WHEN AGE(NOW(), HIRE_DATE) < INTERVAL '10 years' THEN 'Mid-Level'
    WHEN AGE(NOW(), HIRE_DATE) < INTERVAL '20 years' THEN 'Senior'
    ELSE 'Veteran'
  END AS EmploymentStage
FROM Employees;


7.SELECT e.EmployeeID, e.EmployeeName, e.Salary
FROM Employees e
JOIN (
    SELECT DepartmentID, AVG(Salary) AS AvgSalary
    FROM Employees
    GROUP BY DepartmentID
) dept_avg ON e.DepartmentID = dept_avg.DepartmentID
WHERE e.Salary > dept_avg.AvgSalary;


8.SELECT *
FROM Employees
WHERE LOWER(CONCAT(FirstName, LastName)) LIKE '%a%'
  AND Salary % 5 = 0;

9.SELECT 
  DepartmentID,
  COUNT(*) AS TotalEmployees,
  ROUND(
    100.0 * SUM(CASE WHEN AGE(NOW(), HIRE_DATE) > INTERVAL '3 years' THEN 1 ELSE 0 END) / COUNT(*), 2
  ) AS PercentWithMoreThan3Years
FROM Employees
GROUP BY DepartmentID;

10.SELECT JobDescription,
       MIN_BY(SpacemanID, HIRE_DATE) AS MostExperiencedSpaceman,
       MAX_BY(SpacemanID, HIRE_DATE) AS LeastExperiencedSpaceman
FROM Personal
GROUP BY JobDescription;
