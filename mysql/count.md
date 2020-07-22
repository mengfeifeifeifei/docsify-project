**1.**`select distinct a.id,a.name from users a ,users b where a.id<>b.id and a.name=b.name;`

**2.**`select a.name,count(*) count from blog a group by a.name having count>1;`

**3.**`select a.name from blog a where (select count(*) from blog b where b.name=a.name)>1;`


**Count()语法:**

**count(*)---包括所有列，返回表中的记录数，相当于统计表的行数，在统计结果的时候，不会忽略列值为NULL的记录.**

**count(1)---忽略所有列，1表示一个固定值，也可以用count(2)、count(3)代替，在统计结果的时候，不会忽略列值为NULL的记录。**

**count(列名)---只包括列名指定列，返回指定列的记录数，在统计结果的时候，会忽略列值为NULL的记录（不包括空字符串和0），即列值为NULL的记录不统计在内。**

**count(distinct 列名)---只包括列名指定列，返回指定列的不同值的记录数，在统计结果的时候，会忽略列值为NULL的记录（不包括空字符串和0），即列值为NULL的记录不统计在内**