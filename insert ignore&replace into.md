```mysql
insert ignore into actor
values (6, 'ED', 'CHASE', '2006-02-15 12:34:33')

ignore ：如果主键冲突，则忽略本条插入语句


replace into actor
values(3, 'ED', 'CHASE', '2006-02-15 12:34:33')

replace：如果主键冲入，使用插入的记录
```

