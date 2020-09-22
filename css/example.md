## 鼠标拖动选中文字 背景颜色改变
```css
<body>
    <span class="color">鼠标拖动选中文字背景颜色发生改变</span>
</body>

<style>
    .color::selection{
        background: #93c;  // 当鼠标拖动选文字时背景颜色
        color: #fcf;       // 当鼠标拖动选文字时文字颜色
} 
</style>
```

## 两个div标签 一行显示并且分为左右两边
```css
<style>
    .top{
        display: flex;   把div值放到同一行
        flex-direction: row;    div值从左至右显示
        justify-content:space-between;     div值分为一行两边显示
}
    .left{
        margin-left: 15px;   
}
</style>
<div class="top">
    <div class="left">
        xxxxx
    </div>
    <div class="right">
        <span>xxxx</span>
    </div>
</div>
```