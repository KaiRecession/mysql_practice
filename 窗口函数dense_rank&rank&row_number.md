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

