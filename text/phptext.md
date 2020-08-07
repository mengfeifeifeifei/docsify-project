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
> 方法2:
```php
public function twosum(array $nums,$target)
{
    $data = [];
    for($i=0; $i<count($nums); $i++) {
        if($a = array_keys($array,($target-$nums[$i]))) {
            $data[] = [$a[0],$i];
           // return [$a[0],$i];   如果不考虑返回多组值，直接return这个值就可以
        }
        $array[$i] =$nums[$i]; 
    }
    return array_slice($data,-1,1)[0];   // 是为了当数组中出现多组满足条件时的写法
}
```
> 方法3:
```php
public function twosum(array $nums,$target)
{
    $data = [];
    $a = [];
    for($i=0; $i<count($nums); $i++) {
        if(array_key_exists($target-$nums[$i],$data)) {
            $a[] = [$data[$target-$nums[$i]],$i];
        }
        $data[$nums[$i]] = $i;
    }
    return array_slice($a,-1,1)[0];
}
```

` 2.给定一个二叉树，编写函数检验是否相同，在结构且节点都具有相同的值，认为是相同的`

`   1      1                    1    1                          1      1        `

`  / \    / \                  /      \                        / \    / \       `

` 2   3  2   3                2        2                      2   3  3   2      `

`[1,2,3] [1,2,3] true       [1,2]   [1,null,2] false         [1,2,3] [1,3,2] false   ` 

**解题思路：**

**1.递归：如果两个二叉树都为空，那两个二叉树相同。如果两个二叉树中只有一个为空，那肯定不相同。**
**如果两个二叉树都不为空，那就先判断其根节点的值是否相同，如果根节点的值相同，递归去判断其左子树和右子树的值是否相同**
```php
public function isSameTree($p, $q){
    if($p===null && $q===null) {
        return true;
    }else if($p===null || $q===null) {
        return false;
    }else if($p->val != $q->val) {
        return false;
    }else{
        return $this->isSameTree($p->left,$q->left) && $this->isSameTree($p->right,$q->right);
    }
}
```
**2.给一个二叉树的所有节点值加一**
```php
public function sameTree($q){
    if($q == null) {return false;}
    $q += 1;

    sameTree($q->left);
    sameTree($q->right);
}
```

