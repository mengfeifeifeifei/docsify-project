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

> strstr()
```php
// world!  查找"world"在"hello world!"中是否存在，如果在，返回字符串以及剩余的数据
strstr("hello world!","world");  

// 当第三个参数为true时 返回字符串前面的数据
strstr("hello world!","world",true);   // hello
```

> implode()
```php
// 把数组元素合并为字符串  第一个参数为数组合并之后每个元素之间的连接符 默认为""(空字符串)
$arr = array('hello','world');
echo implode(' ', $arr);     // hello world
```

> explode()
```php
// 把字符串拆分为数组  第一个参数规定在字符串的哪里分隔为数组 第三个参数为可选，规定返回数组元素的个数
$str = 'hello world';
print_r(explode(" ",$str));   // array('hello','world');
// 第三个参数
$s = 'hello world BJ';
print_r(explode(" ",$s));    // array([0]=>hello [1]=>world [2]=>BJ);
print_r(explode(" ",$s,0));  // array([0]=>hello world BJ);
print_r(explode(" ",$s,2));  // array([0]=>hello [1]=>world BJ);
```

> break
`break语句可以使流程跳出switch体，只能在循环体内或switch语句、while(){if() break;}中使用break。 break跳出这个switch语句，但不是跳出循环体。break跳出当前这个{} 继续执行{}之外的程序。`

> exit
`exit直接终止程序 其之后的代码不会执行`

> continue
`跳过本次循环，执行下一个循环`

