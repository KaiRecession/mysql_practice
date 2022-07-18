```mysql
select f.film_id, f.title
  from film f left join film_category c
  on f.film_id = c.film_id
  where c.film_id is null;
 
null关键字要使用is判断
```

