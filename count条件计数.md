```mysql
select e.date, round(count(type = 'no_completed' or null) / count(*), 3) from 
 email e where e.send_id not in (select id from user where is_blacklist = 1)
and e.receive_id not in (select id from user where is_blacklist = 1)
 group by date;
 
 select date, count(
  case when (user_id, date) in (select user_id, min(date) from login group by user_id)
    then user_id else null end
) from login
group by date;
```

count本意只能用来统计非null数量后者行数（count（*）），所以条件写成当type不满足就为null，就可以了