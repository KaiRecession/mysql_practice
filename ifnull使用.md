```mysql
select date, ifnull(round(
    count(case when (user_id, DATE_ADD((date),INTERVAL 1 DAY)) in (
        select user_id, date from login) and
          (user_id, date) in (
        select user_id, min(date) from login group by user_id)
          then user_id else null end) / count(case when (user_id, date) in (select user_id, min(date) from login group by user_id) then user_id else null end), 3), 0)
    from login
    group by date;
```

mysql变量的实时使用和条件语句ifnull

```mysql
select ifnull(c.name, 'GroupBuy') as source, count(*) as cnt
    from (
    select client_id, count(*) over(partition by user_id) as cnt
        from order_info
        where product_name in ('Python', 'Java', 'C++') 
        and status = 'completed'
        and date > '2025-10-15'
    ) t left join client c on t.client_id = c.id
    where t.cnt >= 2
    group by c.name
    order by source;
```

null值默认会排在最前面