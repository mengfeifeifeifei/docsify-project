```html
<html>
    <head>
        <meta charset="utf8">
        <style>
            .danci{
                width: 200px;
                height: 200px;
                border: red 1px solid;
                position: relative;
            }
            #text{
                top: 50%;
                left: 50%;
                position: absolute;
                line-height: 50%;
            }
        </style>
        <script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>

        <script src="https://cdn.bootcss.com/toastr.js/latest/js/toastr.min.js"></script>
        <link href="https://cdn.bootcss.com/toastr.js/latest/css/toastr.min.css" rel="stylesheet">   <!--引入样式  -->
    </head>
    <body>
        <div class="danci" >
            <div id="text"></div>
        </div>
        <div>
            <input type="text" id="text1" value=""/>
        </div>
<!--        <button onclick="dianji()">刷新</button>-->
        <button type="submit" onclick="sub()">提交</button>
        <button type="submit" onclick="dianji()">刷新</button>
    </body>
    <script>
        window.onload = function() {
            document.getElementById('text1').focus()           /*当打开页面时  自动定位到input框中 */
            dianji() 
        }
        function dianji(){
            sessionStorage.clear()                            // 设置sessionStorage清空
            var arr = [['我','わたし'],['先生,女士','さん'],['学生','がくせい'],
            ['公司职员','かいしやいん'],['你,您','あなた'],['是,对','はい'],
            ['不,不是','いいえ'],['银行职员','ぎんこういん'],['医生','いしや'],
            ['他,她,那个人','あのかた'],['哪位','どなた'],['大学','だいがく'],
            ['樱花大学','さくらだいがく'],['老师','せんせい'],['几岁','なんさい'],
            ['9','きゆう'],['一岁','一さい'],['初次见面','はじめまして'],
            ['早上好','おはようございます'],['这位是~','こちらは'],['美国','アメリカ'],
            ['是从~来的','からきました'],['来自美国','アメリカからきました'],
            ['请多关照','どうぞよろしく'],['中国','ちゆうごく'],['中国人','ちゆうごくじん'],
            ['教师','きようし'],['他,她那个人','あのひと'],['谁','だれ'],
            ['公司的职员','しやいん'],['富士大学','ふじだいがく'],['巴西','ブラジル'],
            ['8岁','はっさい'],['多大岁数','おいくつ'],['日本','にほん'],
            ['英国','イギリス'],['泰国','タイ'],['德国','ドイツ'],['研究人员','けんきゆうしや'],
            ['神户','こうベ'],['医院','びよういん'],['神户医院','こうベびよういん'],['巴西航空','ブラジルエア一'],
            ['印度','インド'],['韩国','かんこく'],['印度尼西亚','インドネシア'],
            ['对不起,请问','しつれいですが'],['您贵姓,名字','おなまえは'],['动力电气公司','パワ一でんき']];
    
            var a = arr.length-1
            console.log(a)
            var index = Math.round(Math.random()*a);              //  index下标从0 - arr.length-1
            document.getElementById('text').innerText = arr[index][0]
            sessionStorage.setItem('text',arr[index][1]);  
        }

        // 添加监听事件 当在id=text1的input框敲键盘回车时 访问sub()方法  回车的keycode为13
        var input = document.getElementById('text1')   
        input.addEventListener("keyup",function(event){
            event.preventDefault();
            if(event.keyCode === 13) {
                sub()
            }
        })
        function sub(){
            var data = document.getElementById('text1').value
            if(data == sessionStorage.getItem('text')) {          // 用sessionstorage跟用户输入的值对比
                toastr.success('输入正确')
                sessionStorage.clear()
                setInterval(function(){
                    window.location.reload()
                },500);

            }else{
                toastr.error('值错误')
            }
        }

    </script>
</html>
```