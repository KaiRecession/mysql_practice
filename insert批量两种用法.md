```mysql
insert into actor(actor_id,first_name,last_name,last_update)
values (1, 'PENELOPE', 'GUINESS', '2006-02-15 12:34:33'), 
       (2, 'NICK', 'WAHLBERG', '2006-02-15 12:34:33');
       
insert into actor values (1, 'PENELOPE', 'GUINESS', '2006-02-15 12:34:33'),
(2, 'NICK', 'WAHLBERG', '2006-02-15 12:34:33');
两种插入表数据的方式，并且是批量插入

insert ignore into actor
values (3, 'ED', 'CHASE', '2006-02-15 12:34:33')
```

