```mysql
select emp_no, count(*) from salaries
    group by emp_no
    having count(*) > 15;
```

聚合：就是把多行汇总成一行

聚合函数：count，avg等函数，最后变成了一行

聚合键：group by后面的键就是聚合键

书写顺序：select -> from->where->group by->having->order by

内部的执行顺序：from->where->group by->having->order by->select

select只能使用聚合函数和聚合键

having是对组内信息的汇聚，在组间对比

oder是组间排序



group虽然有着限制，但是外面再加一个select的操作就一定能够把数据需要的所有信息拿出来