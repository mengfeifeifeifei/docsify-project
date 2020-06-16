**PDO连接数据库**
```php
{
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

**预处理**
`PDO预处理语句是使用两个方法实现的: prepare()方法负责准备要执行的查询,execute()方法使用一组给定的列参数反复执行查询,再作为数组传递给execute()方法,也可以通过bindParam()方法指定的绑定参数传递给execute()方法`
```php
{
<?php
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
$result->execute();  // 执行
$res = $result->fetch(PDO::FETCH_ASSOC);  (一定要赋值给一个变量 例如$res 否则值取不到)
}
```