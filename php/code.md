**图片验证码**

**1.php**
```php
<?php
    session_start();  // 开启session用来存储验证码的值来去验证用户输入是否正确
    $image = imagecreatetruecolor(100,30);  // 设置画布宽100 高30
    $bgcolor = imagecolorallocate($image, 255,255,255);  // 设置画布的背景颜色
    imagefill($image,0,0,$bgcolor);    // 把背景颜色填充到画布上 从（0,0）开始
    
    // 开始再图片上填写验证码(四位数字)
    /*for($i=0; $i<4; $i++){
        $fontsize = 6;
        $fontcolor = imagecolorallocate($image,rand(0,120),rand(0,120),rand(0,120));
        $fontcontent = rand(0,9);
        $x = ($i*100/4)+rand(5,10); $y = rand(5,10);
        imagestring($image,$fontsize,$x,$y,$fontcontent,$fontcolor); 
    }*/
    
    // 字母数字混合验证码
    $captch_code = '';
    for($i=0; $i<4; $i++) {
        $fontsize = 6; 
        $fontcolor = imagecolorallocate($image,rand(0,120).rand(0,120),rand(0,120));
        $data = 'qwertyuiopasdfghjklzxcvbnm123456789';
        $fontcontent = substr($data, rand(0,strlen($data)-1),1);
        $captch_code .= $fontcontent;
        $x = ($i*100/4)+rand(5,10); $y = rand(5,10);
        imagestring($image,$fontsize,$x,$y,$fontcontent,$fontcolor);
    }   
    $_SESSION['authcode'] = $captch_code;   // 把验证码的结果存入session
    
    // 设置图片上的干扰 （小点）
    for($i=0; $i<200; $i++) {
        $pointcolor = imagecolorallocate($image,rand(50,200),rand(50,200),rand(50,200));
        imagesetpixel($image,rand(1,99),rand(1,29),$pointcolor);    
    }
    // 设置图片上的干扰线
    for($i=0; $i<3; $i++) {
        $linecolor = imagecolorallocate($image,rand(80,220),rand(80,220),rand(80,220));
        imageline($image,rand(1,99),rand(1,29),rand(1,99),rand(29),$linecolor);
    }   
    
    ob_clean();   // 验证码时需要clean一下 不然有时会不显示
    header('content-type:image/jpeg');
    imagejpeg($image);
    
    // 销毁图片 资源
    imagedestroy($image);
```

**1.html**
```html
<body>
    验证码: <img id="image" src="1.php"  style="cursor:pointer;" onclick="onChange()">
            <input type="text" id="butt" placeholder="请输入验证码">
            <button type="submit" onclick="redirect()">Button</button>
</body>
<script>
    function redirect() {
        var a = document.getElementById('butt').value;
        var xml = new XMLHttpRequest();
        xml.open("POST","http://localhost/code/2.php",true);
        xml.onreadystatechange = function() {
           if(xml.readystate == 4 && xml.status == 200) {
            var b = JSON.parse(xml.responseText)    
            if (b.code == 200) {
                alert(b.msg)
            } else if (b.code == 400) {
                alert(b.msg)
            }  else {
                alert('不知道哪错了')
            }      
        }      
      }
        xml.send(JSON.stringify({'a':a}));
    }
    
    function onChange() {
        docuemnt.getElementById('image').src = './1.php'
    }
</script>
```

**2.php**
```php
<?php
session_start();
$input = file_get_contents('php://input');
//print_r($input);
$object = json_decode($input);
if(isset($object->a)) {
    if(strtolower($object->a) == $_SESSION['authcode']) {
        echo json_encode(array("code"=>200,"msg"=>"success"));
    }else {
        echo json_encode(array("code"=>400,"msg"=>"error"));
    }
}
```