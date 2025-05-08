1-SELECT DISTINCT s.CustomerName
FROM #Sales s
WHERE EXISTS (
    SELECT 1
    FROM #Sales sub
    WHERE sub.CustomerName = s.CustomerName
      AND sub.SaleDate >= '2024-03-01'
      AND sub.SaleDate < '2024-04-01'
);
2-select product
from (
    select product, sum(quantity * price) as totalrevenue
    from #sales
    group by product
) as productrevenue
where totalrevenue = (
    select max(sumrevenue)
    from (
        select sum(quantity * price) as sumrevenue
        from #sales
        group by product
    ) as revenues
);

3-select max(saleamount) as secondhighestsale
from (
    select quantity * price as saleamount
    from #sales
) as sales
where saleamount < (
    select max(quantity * price)
    from #sales
);

4-select salemonth, sum(quantity) as totalquantity
from (
    select format(saledate, 'yyyy-MM') as salemonth, quantity
    from #sales
) as monthlysales
group by salemonth;

5-select distinct s1.customername
from #sales s1
where exists (
    select 1
    from #sales s2
    where s1.customername <> s2.customername
      and s1.product = s2.product
);

6-create table #fruit (
    person varchar(100),
    fruit varchar(100)
);

insert into #fruit (person, fruit) values
('alice', 'apple'),
('alice', 'banana'),
('bob', 'apple'),
('bob', 'orange'),
('bob', 'apple'),
('charlie', 'banana');

select person, fruit, count(*) as fruitcount
from #fruit
group by person, fruit;
