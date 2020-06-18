**获取用户ip地址 (原生php函数)**

```php

public function index()
{
    if (!empty($_SERVER["HTTP_CLIENT_IP"])) {
        $cip = $_SERVER["HTTP_CLIENT-IP"];
    } else if (!empty($_SERVER["HTTP_X_FORWARD_FOR"])) {
        $cip = $_SERVER["HTTP_X_FORWARD_FOR"];
    } else if (!empty($_SERVER["REMOTE_ADDR"])) {
        $cip = $_SERVER["REMOTE_ADDR"];
    } else {
        $cip = '';
    }
    
    正则匹配  只匹配一次  当匹配不到时返回false  加ALL一直匹配
    preg_match("/[\d\.]{7,15}/", $cip, $cips);
    $cip = isset($cips[0])? $cips[0] : 'unknown';
    unset($cips);
    return $cip;

}

```