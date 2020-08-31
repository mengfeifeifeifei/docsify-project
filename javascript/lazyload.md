## 页面懒加载 ##
```javascript
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf8">
    </head>
    <script type="text/javascript" src="http://code.jquery.com/jquery-2.1.1.min.js"></script>
    <script type="text/javascript" src="./jquery.lazyload.js"> </script>    // jq的一个懒加载插件
    <body>
        <img alt="" width="640" height="480" data-original="./1.jpg" />
        <img alt="" width="640" height="480" data-original="./1.jpg" />
        <img alt="" width="640" height="480" data-original="./1.jpg" />
        <img alt="" width="640" height="480" data-original="./1.jpg" />
        <img alt="" width="640" height="480" data-original="./1.jpg" />
        <img alt="" width="640" height="480" data-original="./1.jpg" />
        <img alt="" width="640" height="480" data-original="https://img.php.cn/upload/course/000/000/003/5a191001a1fd6838.jpg" />
        <img alt="" width="640" height="480" data-original="https://img.php.cn/upload/course/000/000/003/5a191001a1fd6838.jpg" />
        <img alt="" width="640" height="480" data-original="https://img.php.cn/upload/course/000/000/003/5a191001a1fd6838.jpg" />
        <img alt="" width="640" height="480" data-original="https://atts.w3cschool.cn/attachments/image/20200302/1583146516671855.png" />
        
    </body>
    <script>
        $(function() {
            $("img").lazyload();   // 所有img标签的图片全部都按照懒加载
        })
    </script>   
</html>
```