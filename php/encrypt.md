**client.php**
```php
$public = '-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDa38yZrgZPmy4rIHMhwnv+zJtC
0Nqo493nQyoxl321k0bATrYD9zMqpe+n9L9cUQvlPrDypsw8FsN/aS9EJSY+dDnr
PqhFpWDWpbBRYnRkZns7Rzbv8XVMkpK9j6Z/K95BnEAiPIX0KFMBJ9wQfsfNBPLS
qU8g7BrANcoerwZ2gQIDAQAB
-----END PUBLIC KEY-----';
$local = 'http://localhost/encrypt/serve.php?';

$appkey = "test";
$secretkey = 'answer';

$data = [
    "name" => 'zhang',
    "age"  => 18,
    "password" =>'test',
    "time" => time()
];

$link = http_build_query($data);
$res = get_sign($data, $secretkey);
$link .= "&sign". $res;

$encrypt = "";
openssl_public_encrypt($link,$encrypt,$public);
$encrypt = urlencode($encrypt);
$local .= "q=" $encrypt;

echo $local;

function get_sign($data, $secretkey) {
    ksort($data);
    $a = http_build_query($data);
    $a .= $secretkey;
    return md5($a);
}
```

**server.php**
```php
$private = '-----BEGIN PRIVATE KEY-----
MIICdwIBADANBgkqhkiG9w0BAQEFAASCAmEwggJdAgEAAoGBANrfzJmuBk+bLisg
cyHCe/7Mm0LQ2qjj3edDKjGXfbWTRsBOtgP3Myql76f0v1xRC+U+sPKmzDwWw39p
L0QlJj50Oes+qEWlYNalsFFidGRmeztHNu/xdUySkr2Ppn8r3kGcQCI8hfQoUwEn
3BB+x80E8tKpTyDsGsA1yh6vBnaBAgMBAAECgYEAnMoDA/fQ14ffe89kCkQKlQ03
D5cTfDa3iGnpuNq/l6nn3ezEoHSdt6hk1FkUF+qK7e6JzVlFJqpb41KTJGrESFea
y1sjz7I+OqrTc5yXXvn8pg4XnKeEuB3uEKFjOqMyaOg9Su0dZLTrKo3je6HSkVP0
adMT5xVr9WcBKpYNw0ECQQD1N/gp7PiBe137+QzTGxV+KBvTJ5jpK9hmulb48iml
P+dRJKJGOEWn8XcjwGvQ0uNP2S+aJMOPQDUIGpWamNRpAkEA5H9QMMqpx7yA9kkh
zXVIxV+PkrJKxf5IA9/H7rMXNmvx65TX9xZA2KStxrfn5X51Hs6glLchxWGWTX1c
DbPuWQJAQeIvwtPwUJmcvr5DO9TjCWotT6Yr5znognE+PNSTa9qng52cG9GypVSy
9eAVF54RhLqNl5SZFjviA7NgzpCRQQJBAMCbXLI0Mxctm5t/G+I/id7t5W0nowXw
iS3S1YotJlT2es81ATLDbFfxwJXwcaYuiXU1gYC6OdpSn0qkcBMQ58kCQH3GwXt2
VqVVLTsQn4s36pceo8EXTYc8jrYZYMA65BykO1LWIcoURu6aR6AainDmkFKbasWW
kH+yTjUqBGYgt8w=
-----END PRIVATE KEY-----';
$data = $_GET['q'];
$decrypt = "";
openssl_private_decrypt($data,$decrypt,$private);
$param = [];
parse_str($decrypt,$param);

$sign = get_sign($param);
echo $sign;
if($sign != $data['sign']){
    die('连接被修改');
}else{
    echo 1;
}

function get_sign($data){
    $conf = [
        'ABCDEFG' => 'Test'
    ];

    if(abs($data['time'] - time()) >= 600){
        die('连接超时');
    }

    ksort($data);
    unset($data['sign']);
    $q = http_build_query($data);

    return md5($q.$conf[$data['appkey']]);
    
}
```
