
1-with recursive numbers as (
    select 1 as num
    union all
    select num + 1
    from numbers
    where num < 1000
)
select * from numbers;

2-select e.id, e.name, total_sales
from employees e
join (
    select employee_id, sum(amount) as total_sales
    from sales
    group by employee_id
) s on e.id = s.employee_id;
3-with avg_salary_cte as (
    select avg(salary) as avg_salary
    from employees
)
select * from avg_salary_cte;

4-select p.id, p.name, highest_sale
from products p
join (
    select product_id, max(amount) as highest_sale
    from sales
    group by product_id
) s on p.id = s.product_id;

5-with recursive doubles as (
    select 1 as num
    union all
    select num * 2
    from doubles
    where num * 2 < 1000000
)
select * from doubles;

6-with sales_count as (
    select employee_id, count(*) as sale_count
    from sales
    group by employee_id
    having count(*) > 5
)
select e.name
from employees e
join sales_count s on e.id = s.employee_id;

7-with high_sales as (
    select product_id, sum(amount) as total_sales
    from sales
    group by product_id
having sum(amount) > 500
8-)
select p.*
from products p
join high_sales h on p.id = h.product_id;

with avg_salary as (
    select avg(salary) as avg_sal
    from employees
)
select e.*
from employees e, avg_salary a
where e.salary > a.avg_sal;

9-
