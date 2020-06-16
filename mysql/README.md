**区别**
```mysql
1.select * 和 select字段在性能上没有什么差别
2.网络IO问题
  select * 会查出所有的字段，有些是不需要的，当应用程序和服务器不在同一个局域网时，字段过多会影响网络传输性能
3.索引问题
  select id from table;  
  select *  from table;  
  在id字段有索引的情况下，mysql是不用去数据库中读data数据的,直接使用index（索引）里面的值就返回结果.当用了select * ,其他列需要读取时,就会在读完index之后再去数据库中读data的值.性能消耗
```