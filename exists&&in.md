```mysql

select * from employees e where not exists (
select * from dept_emp where emp_no = e.emp_no
);


区别就是m的n次方和n的m次方哪一个大，外循环大还是内循环大

使用exists关键字进行查询的时候，首先，我们先查询的不是子查询的内容，而是查我们的主查询的表
然后，根据表的每一条记录，依次去判断where后面的条件是否成立


in 和 exists的区别: 如果子查询得出的结果集记录较少，主查询中的表较大且又有索引时应该用in, 反之如果外层的主查询记录较少，子查询中的表大，又有索引时使用exists。其实我们区分in和exists主要是造成了驱动顺序的改变(这是性能变化的关键)，如果是exists，那么以外层表为驱动表，先被访问，如果是IN，那么先执行子查询，所以我们会以驱动表的快速返回为目标，那么就会考虑到索引及结果集的关系了 ，另外IN时不对NULL进行处理。

　　　　in 是把外表和内表作hash 连接，而exists是对外表作loop循环，每次loop循环再对内表进行查询。一直以来认为exists比in效率高的说法是不准确的。
```

