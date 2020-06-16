**鼠标拖动选中文字 背景颜色改变**
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