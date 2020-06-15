#  next
* 地址: `/login`
* 演示地址: [www.baidu.com]
* 请求方式: `POST` [GET post都可以]
* 请求参数

|字段|说明|是否必须|类型|
|--|--|--|--|
|`username`|`mingcheng`|`y`|`string`|

* 返回参数

``` json
{   
    "status":"0001",
     "msg":"success"
}
```


# goend
``` php
{
PDO连接数据库 
$user= "root";                                   //使用的数据库用户名
$pwd= "root";                                    //使用的数据库密码
$host= "localhost";                              //使用的主机名称
$dsn= "$dbms:host=$host;dbname=$dbName";
$pdo=new PDO($dsn,$user,$pwd);                   //初始化一个PDO对象，就是创建了数据库连接对象$pdo
    $query="select * from user";                 //需要执行的sql语句
    $res=$pdo->prepare($query);                  //准备查询语句  //prepare查询  execute执行查询
    $res->execute();                             //执行查询语句，并返回结果集
PDO::FETCH_ASSOC                                 //把数组转化为关系型数组
}
```

# gogoend
```php
{
$dsn = "mysql:host=$db_host;dbname="$db_name";
$pdo = new PDO($dsn,$db_root,$db_pwd);
$query = "select * from users where name=:name,age=:age";
$result = $pdo->prepare($query);  // 执行查询

$result->execute(array(':name'=>'zhang',':age'=>'18'));   // 传递值 并且执行
$result->execute(array(':name'=>'zhang',':age'=>'18'));
或者
$name= '赵明明';
$age = 98;
$result->bindParam(':name',$name);
$result->bindParam(':age',$age);
$result->execute();        // 执行
}
```





