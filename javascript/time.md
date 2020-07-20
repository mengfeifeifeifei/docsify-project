**  **
```javascript
<script type="text/javascript">
    window.onload = function() {
        getData();    
    }
    
    获取时间
    function getData() {
        var date = new Date();
        var date1 = date.toLocaleString();  转换为时间格式  年月日时分秒
        var div1 = docuemnt.getElementById('times');
        div1.innerHTML = date1;
        console.log(date)    
    }
    
    setInterval("getDate()", 1000);
    
    获取星期
    function getWeekend() {
        var a = new Array('日','一','二','三','四','五','六')
        var date = new Date().getDay();
        var str = '今天星期'+a[date];
        var weekend = document.getElementById('weekend')
        weekend.value = str;    
    }      
</script>
```