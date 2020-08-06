## 计算一个数或多个数的乘积
```python
def product(x=0,*args):
    sum = x
    if len(args):
        for i in args:
            sum = sum * i
    return sum
```
```python
def product(x,*args):
    if len(args):
        return x * product(args)
    else:
        return x
```

