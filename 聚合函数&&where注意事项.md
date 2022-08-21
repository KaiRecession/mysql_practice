```mysql
select avg(salary)
    from (
        select salary, max(salary) over() max_s, min(salary) over()  min_s
            from salaries
            where to_date='9999-01-01'
    ) as s1
    where salary not in (s1.max_s, s1.min_s);
    
 窗口函数就是分组 + 排序，每一组的范围就像是一个窗口。over里面可以写partition和order by
 窗口函数是动态的，会以每一个记录行位截止范围运算一次结果。当over里面什么都不写就是全部范围
 
 where里面不能写聚合函数，因为where是在查询前过滤的，聚合函数是对查询结果做聚合的，这不就矛盾了。只有having是对查询后过滤
```

max(case when t.ranking = 1 then t.date else 0 end)

**聚合函数还能这么用**
