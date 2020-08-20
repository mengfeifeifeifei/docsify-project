> 反转字符串 (有空格时数组中加上空格 一般用于有空格的字符串反转等) 
```js
var a = '123456789'; 
console.log(ab.split(''))  // 把字符串拆分为数组 以空间间隔拆开
(9) [0:'1', 1:'2', 2:'3', 3:'4', 4:'5', 5:'6', 6:'7', 7:'8', 8:'9']

数组中顺序颠倒
console.log(ab.split('').reverse())  
(9) [0:'9', 1:'8', 2:'7', 3:'6', 4:'5', 5:'4', 6:'3', 7:'2', 8:'1']

顺序颠倒之后转回字符串  
console.log(ab.split('').reverse().join('')) // 分隔符是什么 join括号中就跟什么   
'987654321'
```

> JSON.stringify()、JSON.parse

`JSON.stringify() 从一个对象中解析出JSON字符串`

```json
JSON.stringify({"a":"1","b":"2"})   // "{"a":"1","b":"2"}"
```

`JSON.parse()从一个JSON字符串中解析出对象`

```json
JSON.parse("{"a":"1","b":"2"}");    // {"a":"1","b":"2"}
```
