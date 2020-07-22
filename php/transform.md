1.`数组转化为对象格式`
```php
function array_to_object($arr) {
    if (gettype($arr) != 'array') {
        return;
    }
    foreach ($arr as $k => $v) {
        if (gettype($v) == 'array' || getType($v) == 'object') {
            $arr[$k] = (object)array_to_object($v);
        }
    }
    return (object)$arr;
} 

/* stdClass Object ( [ret] => 0 [msg] => [is_lost] => 0 [nickname] => 十 
[gender] => 男 [gender_type] => 1 [province] => 吉隆坡 
[city] => [year] => 1999 [constellation] =>  
[figureurl_type] => 1 [is_yellow_vip] => 0 [vip] => 0 
[yellow_vip_level] => 0 [level] => 0 [is_yellow_year_vip] => 0 [uname] => 十 )   */
```

2.`对象转化为数组`
```php
function object_to_array($obj) {
    $obj = (array)$obj;
    foreach ($obj as $k => $v) {
        if(gettype($v) == 'resource') {
            return;
        }
        if(gettype($v) == 'object' || gettype($v) == 'array') {
            $obj[$k] = (array)object_to_array($v);
        }
    }
    return $obj;
}
```