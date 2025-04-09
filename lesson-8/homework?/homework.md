1-select category, count(*) as TotalProducts
from Products
group by category;

2-select avg(Price) as AveragePrice
from products
where category = 'Electronics';

3-select customerName, City
from Customers
where City ike 'L%';

4-select ProductName
from Products
where ProductName like '%er';

5-select customerName, Country
from Customers
where Country like '%A';

6-select max(Price) as HighestPrice
from Products;

7-select ProductName, 
if(Quantity < 30, 'Low Stock', 'Sufficient') as StockStatus
from Products;

8-select Country, count(*) as TotalCustomers
from customers
group by country;

9-select min(Quantity) as MinQuantity, max(Quantity) as MaxQuantity
from Orders;


