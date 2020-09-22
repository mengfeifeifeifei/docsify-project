**轮播图(自动加载)**
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .banner {
            position: relative;
            width: 100%;
            height: 300px;
            text-align: center;
            float: left;
        }
        .item {
            /*display: none;*/
            position: absolute;
            width: 100%;
            height: 300px;
            top: 0;
            left: 0;
        }
        ul {
            list-style-type: none;
            margin:0;
            padding:0;
        }
        .lunbo {
            width: 100%;
            height: 300px;
        }
        .lr-tab .btn{
            position: absolute;
            top: 120px;
            width: 100px;
            height: 69px;
        }
        .lr-tab .left{
            left: 0px;
            background-position-x: -83px;
            background: url("./left.jpg");
            background-size: 100px 50px;    /* 100 为宽    50为高 */
            background-repeat: no-repeat;    /*  设置不重复 */
            cursor:pointer;                 /*  设置小手效果 */
        }
        .lr-tab .right{
            right: 0px;
            background-position-x: -125px;
            background: url("./right.png");
            background-size: 100px 50px;
            background-repeat: no-repeat;
            cursor:pointer;
        }
        /*左右按钮触碰事件*/
        .lr-tab .left:hover{
            /*background-position-x: 0px;*/
        }
        .lr-tab .right:hover{
            /*background-position-x: -41px;*/
        }
    </style>
    <script
            src="https://code.jquery.com/jquery-3.3.1.js"
            integrity="sha256-2Kok7MbOyxpgUVvAk/HJ2jigOSYS2auK4Pfzbm7uH60="
            crossorigin="anonymous"></script>
</head>
<body>
    <div class="banner">
        <div class="img-wrap">
            <ul>
                <li class="item">
                    <a href=""><img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1600762518377&di=442d0d9e5454444a120a499962c3fddd&imgtype=0&src=http%3A%2F%2Fa3.att.hudong.com%2F14%2F75%2F01300000164186121366756803686.jpg" alt="" class="lunbo"></a>
                </li>
                <li class="item">
                    <a href=""><img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1600763474663&di=358758caa481057f9a09e1ba8461ef6d&imgtype=0&src=http%3A%2F%2Ft8.baidu.com%2Fit%2Fu%3D2247852322%2C986532796%26fm%3D79%26app%3D86%26f%3DJPEG%3Fw%3D1280%26h%3D853" alt="" class="lunbo"></a>
                </li>
                <li class="item">
                    <a href=""><img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1600765451513&di=1a58c2808aa96a96536725d3dd806e0a&imgtype=0&src=http%3A%2F%2Fa4.att.hudong.com%2F52%2F52%2F01200000169026136208529565374.jpg" alt="" class="lunbo"></a>
                </li>
                <li class="item">
                    <a href=""><img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1600765489272&di=885e037a1cd65af329484bc2568de321&imgtype=0&src=http%3A%2F%2Fa1.att.hudong.com%2F05%2F00%2F01300000194285122188000535877.jpg" alt="" class="lunbo"></a>
                </li>
            </ul>
        </div>
        <div class="lr-tab">
            <div class="left btn"></div>     <!--  左右两侧切换轮播图图片  -->
            <div class="right btn"></div>
        </div>
        <div class="tab-btn">
            <ul>
                <li class="btn"></li>
                <li class="btn"></li>
                <li class="btn"></li>
                <li class="btn"></li>
            </ul>
        </div>
    </div>
</body>
<script type="text/javascript">
    window.onload = function(){
        $(".item").eq(0).fadeIn().siblings().hide();
    }
    var index2 = 0;/*初始化一个变量 指向下彪*/
    //点击点
        $(".tab-btn .btn").click(function () {
        index2 = $(this).index();//获取点击该元素下彪
            console.log(index2)
        $(this).addClass("active").siblings().removeClass("active");
        $(".item").eq(index2).fadeIn().siblings().fadeOut();      /* eq是去数组中寻找第几个元素 eq(2) 代表去找item中第三个数据   fadein 是淡入效果来隐藏一个元素（对应的fadeout是淡出）
                                                             当siblings('xxx')中添加了选择器之后，就去找所有.item下类名为xxx的元素设置淡出效果。 如果没有加()括号中的值就去找.item选择器下其他的元素设置淡出效果 */
    });
    //点击切换效果
    $(".lr-tab .right").click(function () {
        index2 ++;
        console.log(index2)
        if (index2 >3){ index2 = 0;}
        console.log(index2)
        $(".item").eq(index2).fadeIn().siblings().fadeOut();
        $(".tab-btn .btn").eq(index2).addClass("active").siblings().removeClass("active");

    });
    $(".lr-tab .left").click(function () {
        index2 --;
        console.log(index2)
        if(index2 < 0){index2 = 3;}
        console.log(index2)
        $(".item").eq(index2).fadeIn().siblings().fadeOut();
        $(".tab-btn .btn").eq(index2).addClass("active").siblings().removeClass("active");

    });
    var time2 = setInterval(function () {
        index2 ++;
        if (index2 >3){ index2 = 0;}
        $(".item").eq(index2).fadeIn().siblings().fadeOut();
        $(".tab-btn .btn").eq(index2).addClass("active").siblings().removeClass("active");
    },4000); //定时器 重复
</script>

</html>


```