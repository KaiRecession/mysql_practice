```mysql
delete from titles_test
    where id not in (select * from (
        select min(id) from titles_test
            group by(emp_no)
    ) as t1);
    
mysql不能够边查询变删除，所以要先建一个视图表，再从表中选择
delete就是直接删除一整行，就不用选字段，where指定删除条件
```

