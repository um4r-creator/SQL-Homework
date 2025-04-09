1-select min(Price) as MinPrice
from products;

2-select max(Salary) as maxsalary
from Employees;

3-select count(*) as Numberofcustomers
from Customers;

4-select count(distinct Category) as UniqueCategories
from Products;

5-select avg(Age) as AverageAge
from employees;

6-select avg(Age) as AverageAge
from employees;

7-select DeptID, count(*) as NumberOfEmployees
from Employees
group by DeptID;

8-select category,,min(Price) as MinPrice, max(Price) as MaxPrice
from Products
grou by category;

9-select CustomerID, sum(SalesAmount) as TotalSales
FROM Sales
group by customerID;

10-select DeptID, count(*) as NumberOfEmployees
from employees
group by DeptID
having count(*) > 5;











