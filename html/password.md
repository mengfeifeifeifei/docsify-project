**密码显示隐藏控制**
```html
<html>
<head>
    <meta charset="utf8">
</head>
<script>
    var isshow = true;    
    function change() {
        var status = document.getElementById("ps");
        if(isshow) {
            status.type="text"
            isshow=false
            document.getElementById("show").innerText = "隐藏密码"     
        } else {
            status.type="password"
            isshow=true
            document.getElementById("show").innerText = "显示密码"
        }   
}
</script>
<body>
    <button onclick="change()" id="show">显示密码</button>
    <input type="password" id="ps">
</body>
</html>
```


```html
<html>
<head>
    <meta charset="utf8">
</head>
<script>
    window.onload=function(){
                  var btn=document.getElementById("btn");
                  var pass=document.getElementById("pass")
                  btn.onmousedown=function(){
                         pass.type="number"
                         };
                  btn.onmouseup=btn.onmouseout=function(){
                          pass.type="password"
                         }
                  }
</script>
<body>
<input type="button" name="" id="btn" value="点击显示" />
<input type="password" id="pass">
</body>
</html>
```