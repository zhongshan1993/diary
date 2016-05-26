# javascript解决leetcode算法题 #

## 统计“1”的个数

给定一个非负整数 num，对于任意 i，0 ≤ i ≤ num，计算 i 的值对应的二进制数中 “1” 的个数，将这些结果返回为一个数组。

```
function countBit(n){  
  return n.toString(2).replace(/0/g,"").length;
}

function countBits(nums){  
  var ret = [];  
  for(var i = 0; i <= nums; i++){
    ret.push(countBit(i));
  } 
  return ret;
}
```