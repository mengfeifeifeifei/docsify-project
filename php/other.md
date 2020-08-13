
## 获取文件的根目录位置


**文件位置 D:\phpstudy\PHPTutorial\WWW\ceshi.php**  

`dirname(__FILE__) // 获取该文件的根目录位置`

`__FILE__;  // D:\phpstudy\PHPTutorial\WWW\ceshi.php;`

`__DIR__;   // D:\phpstudy\PHPTutorial\WWW;`

`__dirname(__FILE__);  // D:\phpstudy\PHPTutorial\WWW;`

`dirname(dirname(__FILE__)); // D:\phpstudy\PHPTutorial`

## 根据用户的经纬度查询数据库中附近经纬度的数据(就近原则)

```php
public function testMapDispose()
{
        // 接受前台传来的值
        $params = $this->request->post();

        $session_id = $params['session_id'];
        DB::name('shengfaapp_around_hospital_times')->insert(['session_id'=>$session_id]);

        $Provinces = $params['province'];
        $Citys = $params['city'];
        $longitude = $params['longitude']; //经度
        $latitude = $params['latitude'];  // 纬度
        $lng=floatval($longitude);//用变量替换时注意数据类型
        $lat=floatval($latitude); 
        // 腾讯地图经纬度转化为百度地图经纬度方法
        $locXY=$this->Convert_GCJ02_To_BD09($lng,$lat); 
        $lng = $locXY['lng'];
        $lat = $locXY['lat'];

        $provinceALL = DB::name('hospital')->where('city', 'like', "%$Provinces%")->select();
        $cityALL = DB::name('hospital')->where('city', 'like', "%$Citys%")->select();
        $ca = [];
        if (!empty($cityALL)) {
            foreach($cityALL as $key=>$val){
                // 把数据库中的经纬度字段拆分为数组
                $data = explode(',',$val['lngandlat']);
                if($data) {
                    if (count($data) < 2) {
                        continue;
                    } else {
                        $distance = $this->zhang($lat, $lng, $data[1], $data[0]);
                        $ca[$key]['distance'] = $distance;
                        $unit = '';
                        if($distance < 1000){
                            $unit = $distance . '米';
                        }
                        if($distance >= 1000){
                            $unit = round($distance / 1000, 2) . '千米';
                        }
                        $ca[$key]['id'] = $val['id'];
                        $ca[$key]['name'] = $val['name'];
                        $ca[$key]['address'] = $val['address'];
                        $ca[$key]['city'] = $val['city'];
                        $ca[$key]['lngandlat'] = $val['lngandlat'];
                        $ca[$key]['doctor'] = $val['doctor'];
                        $ca[$key]['visits'] = $val['visits'];
                        $ca[$key]['professionaltitle'] = $val['professionaltitle'];
                        $ca[$key]['distance_unit'] = $unit;
                    }
                }
            }
            // 把数组按照字段(距离) 'distance'  排序   就近原则
            array_multisort(array_column( $ca, 'distance'), SORT_ASC, $ca);
            $hide = "none";
            $arr = array($hide, $ca);
            return json($arr);
        } elseif (!empty($provinceALL)) {
            foreach($provinceALL as $key=>$val){
                $data = explode(',',$val['lngandlat']);
                if($data) {
                    if (count($data) < 2) {
                        continue;
                    } else {
                        $distance = $this->zhang(39.934772151572, 116.42277272333, $data[1], $data[0]);
                        $ca[$key]['distance'] = $distance;
                        $unit = '';
                        if($distance < 1000){
                            $unit = $distance . '米';
                        }
                        if($distance >= 1000){
                            $unit = round($distance / 1000, 2) . '千米';
                        }
                        $ca[$key]['id'] = $val['id'];
                        $ca[$key]['name'] = $val['name'];
                        $ca[$key]['address'] = $val['address'];
                        $ca[$key]['city'] = $val['city'];
                        $ca[$key]['lngandlat'] = $val['lngandlat'];
                        $ca[$key]['doctor'] = $val['doctor'];
                        $ca[$key]['visits'] = $val['visits'];
                        $ca[$key]['professionaltitle'] = $val['professionaltitle'];
                        $ca[$key]['distance_unit'] = $unit;
                    }
                }
            }
            array_multisort(array_column( $ca, 'distance'), SORT_ASC, $ca);
            $hide = "none";
            $arr = array($hide, $ca);
            return json($arr);
        } else {
            $hide = "block";
            $arr = array($hide);
            return json($arr);
        }
}

/**
 * 中国正常GCJ02坐标-->百度地图BD09坐标
 * 腾讯地图用的也是GCJ02坐标
 * @param double $lng 经度
 * @param double $lat 纬度
 */
public function Convert_GCJ02_To_BD09($lng,$lat)
{
    $x_pi = 3.14159265358979324 * 3000.0 / 180.0;
    $x = $lng;
    $y = $lat;
    $z =sqrt($x * $x + $y * $y) + 0.00002 * sin($y * $x_pi);
    $theta = atan2($y, $x) + 0.000003 * cos($x * $x_pi);
    $lng = $z * cos($theta) + 0.0065;
    $lat = $z * sin($theta) + 0.006;
    return array('lng'=>$lng,'lat'=>$lat);
}

public function zhang($lat1, $lon1, $lat2, $lon2)
{
 // 求出用户经纬度和数据库经纬度之间的距离 
    $distance = ROUND(6378.138 * 2 * ASIN(SQRT(POW(SIN(($lat1 * PI() / 180 - $lat2 * PI() / 180) / 2),2) + COS( $lat1 * PI() / 180) * COS($lat2 * PI() / 180) * POW(SIN(($lon1 * PI() / 180 - $lon2 * PI() / 180) / 2),2)))*1000);
    return $distance;
}
```

## 文件上传(单文件)
```php
<?php
// myfile为html中 input框中的name值  <input type="file" name="myfile" />
$fileInfo = $_FILES['myfile'];

function uploadFile($fileInfo,$flag=true,$allowExt=array('jpg','png','jpeg','gif'),$maxSize=2097152,$uploadPath='uploads') {
    if($fileInfo['error'] > 0) {
        switch($fileInfo['error']){
            case 1 :
                $msg =  '上传文件超过配置文件中upload_max_filesize';
                break;
            case 2 :
                $msg =  '超过表单MAX_FILE_SIZE限制的大小';
                break;
            case 3 :
                $msg =  '文件部分被上传';
                break;
            case 4 :
                $msg =  '没有上传文件';
                break;
            case 6 :
                $msg =  '没有找到临时目录';
                break;
            case 7 :
                $msg =  'no';
                break;
            case 8 :
                $msg =  '系统错误';
                break;
        }
        exit($msg);
    }

    // 检测文件上传类型
    //  $allowExt = array('jpg','png','jpeg','gif');
    $ext = pathinfo($fileInfo['name'],PATHINFO_EXTENSION);
    if(!in_array($ext,$allowExt)) {
        exit('非法文件类型');
    }

    // 检测上传文件的大小
    //$maxSize = 2097152;  //2M
    if($fileInfo['size'] > $maxSize) {
        exit('上传文件过大');
    }

    // 检测文件是否是通过post方式上传
    if(!is_uploaded_file($fileInfo['tmp_name'])) {
        exit('上传文件不是post上传');
    }

    // 检测是否为真实图片类型
    if($flag){
        if(!getimagesize($fileInfo['tmp_name'])) {
            exit('文件不是真实的图片类型');
        }
    }
    
    // 判断是否有文件uploads 没有的话创建
    //$uploadPath = "uploads";
    if(!file_exists($uploadPath)) {
        mkdir($uploadPath,0777,true);
        chmod($uploadPath,0777);
    }
    // 生成唯一的文件名
    $filename = $uploadPath.'/'.md5(uniqid(microtime(true),true)).'.'.$ext;
    if(!@move_uploaded_file($fileInfo['tmp_name'],$filename)) {
        exit('文件上传失败');
    }

    return array(
        'newName' => $filename,
        'size' => $fileInfo['size']
    );
    
}
```
> 图片下载
```php
// 在php文件中 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
<a href="./download.php?filename=https://dss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3445812423,773927785&fm=26&gp=0.jpg">下载图片</a>
</body>
</html>
// 接受的文件
$a = $_GET['filename'];
header("Content-Disposition:attachment;filename=\"$a\"");   //  \转义的意思是因为图片中有','所以需要转义 ，图片地址可以为本地相对路径
header('content-length:'.filesize($a));
readfile($a);
```