-- get all unique regions and distributors
with regions as (
    select distinct region from #RegionSales
),
distributors as (
    select distinct distributor from #RegionSales
)

-- cross join and left join to actual sales
select 
    r.region,
    d.distributor,
    coalesce(rs.sales, 0) as sales
from regions r
cross join distributors d
left join #RegionSales rs
    on rs.region = r.region and rs.distributor = d.distributor
order by d.distributor, r.region;

2-select 
    e.name as manager_name,
    count(*) as direct_reports
from employee emp
join employee e on emp.managerid = e.id
group by e.name
having count(*) >= 5;

3-SELECT 
    p.product_name,
    SUM(o.unit) AS total_units
FROM 
    Products p
JOIN 
    Orders o ON p.product_id = o.product_id
WHERE 
    o.order_date >= '2020-02-01' AND o.order_date < '2020-03-01'
GROUP BY 
    p.product_name
HAVING 
    SUM(o.unit) >= 100;

