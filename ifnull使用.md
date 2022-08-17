```mysql
select date, ifnull(round(
    count(case when (user_id, DATE_ADD((date),INTERVAL 1 DAY)) in (
        select user_id, date from login) and
          (user_id, date) in (
        select user_id, min(date) from login group by user_id)
          then user_id else null end) / count(case when (user_id, date) in (select user_id, min(date) from login group by user_id) then user_id else null end), 3), 0)
    from login
    group by date;
```

mysql变量的实时使用和条件语句ifnull