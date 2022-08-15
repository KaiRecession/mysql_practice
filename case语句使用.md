```mysql
select e.emp_no, e.first_name, e.last_name, b.btype, s.salary, 
case when b.btype = 1 then s.salary * 0.1
    when b.btype = 2 then s.salary * 0.2
    else s.salary * 0.3
    end
    from (
        select * from salaries where to_date = '9999-01-01'
    ) as s inner join employees e on s.emp_no = e.emp_no
    inner join emp_bonus as b on s.emp_no = b.emp_no;
    
    case when then
    	when then
    	...
    	else 
    	end
```

