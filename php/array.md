## 数组排序
`sort()   对数组中的元素进行升序排列 `
```php
sort(array("Volvo","BMW","Toyota"));

Array ( [0] => BMW [1] => Toyota [2] => Volvo )
```
`rsort()  对数组中的元素进行降序排列 `
```php
rsort(array("Volvo","BMW","Toyota"));

Array ( [0] => Volvo [1] => Toyota [2] => BMW )
```
`asort()  按数组中的值 对数组进行升序排列`
```php
asort(array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43"));

Array ( [Peter] => 35 [Ben] => 37 [Joe] => 43 )
```
`ksort()  按数组中的键 对数组进行升序排列`
```php
ksort(array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43"));

Array ( [Ben] => 37 [Joe] => 43 [Peter] => 35 )
```
`arsort()  按数组中的值 对数组进行降序排列`
```php
arsort(array("Peter"=>"35","Ben"=>"37","Joe"=>"43"));

Array ( [Joe] => 43 [Ben] => 37 [Peter] => 35 )
```
`krsort()  按数组中的键 对数组进行降序排列`
```php
krsort(array("Peter"=>"35","Ben"=>"37","Joe"=>"43"));

Array ( [Peter] => 35 [Joe] => 43 [Ben] => 37 )
```
`array_sum()  求数组中所有值得和`
```php
array_sum(range(1,100));   //1-100的和
```