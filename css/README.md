## Background
`background-position-x: -83px;` **设置背景定位x轴的参数**

`background: url("./left.jpg");` **背景图片**

`background-size: 100px 50px;`   **背景图片大小** /* 100 为宽    50为高 */

`background-repeat: no-repeat;`  **是否重复显示**

## cursor(设置鼠标放上去时显示不同的光标)
`cursor:pointer` **手样式**

`cursor:auto/text/`    **普通的I形**

`cursor:wait`    **圈形等待**

`cursor:help`    **箭头旁带问号**

`cursor:move`    **十字形移动形**

`cursor:default` **普通的箭头形**

## transition、transform
**用来logo墙的图片放大时案例(鼠标放到图片上时0.6s放大到1.3倍)**
```css
.img_size {
    width:70px; height: 70px;
    cursor:pointer;
}
.img_size:hover {
    transform: scale(1.3);
    translation:all 0.6s;
}
```
