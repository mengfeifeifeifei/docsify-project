
**在这里 不能使用where来进行筛选, 因为表中不存在SUM(bbb)的记录,所以使用Having来筛选数据
    Having单独使用 和 where一样**
```mysql
select region,SUM(aaaaa),SUM(bbb) from abc group by region Having SUM(bbb)>10
```