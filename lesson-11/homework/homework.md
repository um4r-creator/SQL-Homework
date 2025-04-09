1-select O.OrderID, C.CustomerName, O.OrderDate
from Orders O
join Customers C on O.CustomerID = C.CustomerID
where O.OrderDate > '2022-12-31';

2-select E.EmployeeName, D.DepartmentName
from Employees E
join Departments D on E.DepartmentID = D.DepartmentID
where D.DepartmentName IN ('Sales', 'Marketing');

3-select D.DepartmentName, E.EmployeeName as TopEmployeeName, max(E.Salary) as MaxSalary
from Departments D
join Employees E ON D.DepartmentID = E.DepartmentID
group by D.DepartmentName;

4-select C.CustomerName, O.OrderID, O.OrderDate
from Customers C
join Orders O on C.CustomerID = O.CustomerID
where C.Country = 'USA' and YEAR(O.OrderDate) = 2023;

5-select C.CustomerName, O.OrderID, O.OrderDate
from Customers C
join Orders O ON C.CustomerID = O.CustomerID
where C.Country = 'USA' and YEAR(O.OrderDate) = 2023;

6-select P.ProductName, S.SupplierName
from Products P
join Suppliers S on P.SupplierID = S.SupplierID
where S.SupplierName in ('Gadget Supplies', 'Clothing Mart');

7-select C.CustomerName, max(O.OrderDate) as MostRecentOrderDate, O.OrderID
from Customers C
left join Orders O ON C.CustomerID = O.CustomerID
group by C.CustomerName, O.OrderID;
