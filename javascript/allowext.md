**js检测上传文件类型**
```javascript
var AllImgExt=".jpg|.jpeg|.bmp|.png|";   // 定义一个允许上传的类型

let files = $("#img-file")[0].files;   // 获取上传文件
var allowExt = checkFileType(files[0])  // 传值 
if (allowExt) {xxxxx} else {xxxxx}
function checkFileType(file) {
    var playIndex = String(file.name).lastIndexOf(".");    // 得出'.'在file.name中最后一次出现的索引位置 
    var playid = String(file.name).substring(playIndex);   // 截取从playIndex位置之后的所有字符
    if(AllImgExt.indexOf(playid+"|") == -1) {      // indexof()中填写得到的类型，去AllImgExt中查询  如果没有说明不符合 会返回-1
        return false;
    }else {
        return true;
    }
}
```