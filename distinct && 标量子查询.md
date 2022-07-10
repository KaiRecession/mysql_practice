```mysql
select * from employees where hire_date = 
    (select distinct hire_date from employees
        order by hire_date desc
        limit 2, 1);
标量子查询就是指子查询的结果是“单个值”（一行一列）的查询。
在对字段进行去重的时候，要保证distinct在所有字段的最前面
如果distinct关键字后面有多个字段时，则会对多个字段进行组合去重，只有多个字段组合起来的值是相等的才会被去重
select count(distinct name,age) as total from user;
```

