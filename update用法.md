```mysql
update titles_test
    set to_date = null, from_date = '2001-01-01'
    where to_date = '9999-01-01';
   
 update 不需要from，set设置多个字段
```

