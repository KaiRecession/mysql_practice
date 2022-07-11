```mysql
select salaries.*, dept_manager.dept_no from salaries join dept_manager on salaries.emp_no = dept_manager.emp_no;

select e.last_name, e.first_name, d.dept_no from 
    employees as e inner join dept_emp as d （as 可以省略）
    on e.emp_no = d.emp_no;

left 就是以语句中左边那个表为老大，匹配，老大没有匹配上的显示null
on条件是在生成临时表时使用的条件，它不管on中的条件是否为真，都会返回左边表中的记录。
where条件是在临时表生成好后，再对临时表进行过滤的条件。这时已经没有left join的含义（必须返回左边表的记录）了，条件不为真的就全部过滤掉。
但其实on就是用在多表链接时候的条件，where就不适合，on才可以生成为null的记录，where就不能，where适合单表的查询条件
inner join on 就适合多表查询的时候进行连接，适合多个集合之间的匹配，where就适合一个集合中的查找。只有用了多表联合才能够同时显示两个表的列数据
```

