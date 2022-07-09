```mysql
select * from employees
    order by hire_date desc
    limit 1;  从头开始数一行
select * from employees
    order by hire_date desc
    limit 0, 1;  从索引第0个记录，往后数一行（效果和上面一样）
select * from employees
    order by hire_date desc
    limit 1 offset 0; 偏移就是起始点
```

