> Invtal ceil 
```php
ceil函数向上舍入最接近的整数
intval(ceil($count / $limits));
返回不小于X的下一个整数，X如果有小数部分则进一位。ceil() 返回的类型仍然是float，因为float值得范围通常比integer要大。
例: echo(ceil(0.40));      1
    echo(ceil(5));         5
    echo(ceil(5.1));       6
    echo(ceil(-5.1));     -5
    echo(ceil(-5.9));     -5
    echo(ceil(-5.9));     -5
    echo(ceil(0.60));      1
```

> Strpos 
```php
查询'a'在数组$arr中出现第一次的位置，没有出现返回false.
strpos($arr, 'a');
=== 判断变量类型和值完全相等
==  判断变量的值相等
```

> Substr
```php
substr('string',start, length);     // length 为可选参数.
substr()函数返回字符串的一部分.
例: substr('hello world',6);        // world
```

> Compact
```php
compact('a', 'b');    // 创建一个包含变量名和它们的值的数组
例:
$a = 'admin';     $b = '123456';   compact('a', 'b');     // array('a'=>'admin','b'=>'123456');
```

> parse_str(string,array)
```php
parse_str("name=Peter&age=43"); echo $name; echo $age;  (Peter 43)
当array传值时
parse_str("name=Peter&age=43",$array);  (Array([name]=>peter [age]=>43));
```

> str_replace()
```php
<?php
// 把字符串hello world 中字符 'world'替换成 'peter'
echo str_replace("world","Peter","Hello world!");
?>
str_replace()第四个参数为可选参数, 对替换数进行计数,例如上边计数为1
```

> file_put_content()
```php
<?php
// 把$data数据追加写入到 text.txt文件中
file_put_content('./text.txt', $data, FILE_APPEND);
// 把$data数据追加写入到text文件中 并且换行
file_put_content('./text.txt', $data.PHP_EOL, FILE_APPEND);
```

> json_decode  、json_encode

`当第二个参数为true时返回array, 默认是false 返回object`

```php
json_decode()    -- json转 对象/数组
```

`成功返回json编码的string, 失败返回false`

```php
json_encode()    -- 对象/数组 转json
```

> JSON.stringify()、JSON.parse

`JSON.stringify() 从一个对象中解析出JSON字符串`

```json
JSON.stringify({"a":"1","b":"2"})   // "{"a":"1","b":"2"}"
```

`JSON.parse()从一个JSON字符串中解析出对象`

```json
JSON.parse("{"a":"1","b":"2"}");    // {"a":"1","b":"2"}
```
