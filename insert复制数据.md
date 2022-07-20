```mysql
create table actor_name (
  first_name varchar(45) not null,
  last_name varchar(45) not null
);
insert into actor_name
(select first_name, last_name from actor);

insert从其他表中复制数据插入本表
```

