```mysql
select emp_no, salary, dense_rank() over (order by salary desc) as t_rank
 from salaries
 order by salary desc, emp_no;
 
1、RANK()
在计算排序时，若存在相同位次，会跳过之后的位次。
例如，有3条排在第1位时，排序为：1，1，1，4······

2、DENSE_RANK()
这就是题目中所用到的函数，在计算排序时，若存在相同位次，不会跳过之后的位次。
例如，有3条排在第1位时，排序为：1，1，1，2······

3、ROW_NUMBER()
这个函数赋予唯一的连续位次。
例如，有3条排在第1位时，排序为：1，2，3，4······

select t1.emp_no, t1.salary, count( distinct t2.salary) as t_rank
from salaries t1,salaries t2
where t1.salary <= t2.salary
group by t1.emp_no,t1.salary
order by t1.salary desc, t1.emp_no

where 居然连接两张表的时候也是笛卡尔积
```

## 窗口函数

基本语法

```sql
<窗口函数> OVER ([PARTITION BY <列清单>] ORDER BY<排序清单>)
```

能够作为窗口函数的函数

1、SUM、AVG、COUNT、MAX、MIN（聚合函数）

2、RANK、DENS_RANK、ROW_NUMBER等专用窗口函数

窗口函数配合起来就可以先分组，然后组内排序。PARTITION BY就是分组，分完组就是一个个窗口

当使用聚合函数的时候就可以实现累计求和或者累计求平均等等

```mysql
select emp_no, salary, sum(salary) over (order by emp_no) from salaries
    where to_date = '9999-01-01';
```

**窗口函数使用了partition和over后，原本表的顺序就已经按照分区排好序了**
