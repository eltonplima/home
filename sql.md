Distinct names from two different tables

```sql
select distinct name from (
  select name from dogs
  union
  select name from cats
) t
```
