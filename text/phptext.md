` 1. 给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。`


>示例:

**给定 nums = [2, 7, 11, 15], target = 9**

**因为 nums[0] + nums[1] = 2 + 7 = 9**
**所以返回 [0, 1]**
> 方法1(效率低)：
```php
/**
     * @param Integer[] $nums   [2, 7, 11, 15]
     * @param Integer $target   9
     * @return Integer[]
*/  
public function twosum(array $nums,$target)
{
    $data = [];
    for($i=0; $i<count($nums); $i++) {
        for($j=$i+1; $j<count($nums); $j++) {
            if($nums[$i] + $nums[$j] == $target) {
                //return [$i,$j];   
                $data[] = [$i,$j];   // 此处用data保存是因为数据中不一定只有一组满足条件的，当出现很多组都可以满足相加等于9的时候，再最后return取了最后一组数据
            }
        }
    }
    return array_slice($data,-1,1)[0];  // $nums中不论有一组或多组满足条件的，都可以返回，多组时只返回最后一组。
}
```

