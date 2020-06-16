**输入框中提示语显示**
```javascript
1.当点击输入框时 提示语消失 当无输入鼠标点出时  提示语会再次出现
  <input type="text" value="请输入要查找的关键字" onfocus="if(value=='请输入要查找的关键字')value=''" onblur="if(!value)value='请输入要查找的关键字'" name="keyword" >
```

```javascript
2.当点击输入框时提示语消失  刷新页面再次出现
  <input type="text" value="请输入内容" onfocus="javascript:if(this.value=='请输入内容') this.value=''>
```