1-select e.EmployeeName, e.Salary, d.DepartmentName
from Employees e
join Departments D on E.DepartmentID = D.DepartmentID
where E.Salary > 50000;

2-select C.FirstName, C.LastName, O.OrderDate
from Customers C
join Orders O ON C.CustomerID = O.CustomerID
where year(O.OrderDate) = 2023;r

3-select E.EmployeeName, D.DepartmentName
from Employees E
left join Departments D on E.DepartmentID = D.DepartmentID;

4-select S.SupplierName, P.ProductName
from Suppliers S
left join Products P on S.SupplierID = P.SupplierID;

5-select O.OrderID, O.OrderDate, P.PaymentDate, P.Amount
from Orders O
left join Payments P on O.OrderID = P.OrderID;

6-select E.EmployeeName, M.EmployeeName AS ManagerName
from Employees E
lwft join Employees M on E.ManagerID = M.EmployeeID;

7-select S.StudentName, C.CourseName
from Students S
join Enrollments E on S.StudentID = E.StudentID
join Courses C ON E.CourseID = C.CourseID
where C.CourseName = 'Math 101';
