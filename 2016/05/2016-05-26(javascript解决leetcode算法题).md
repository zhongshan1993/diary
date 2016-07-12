# javascript解决leetcode算法题 #

## 统计“1”的个数

给定一个非负整数 num，对于任意 i，0 ≤ i ≤ num，计算 i 的值对应的二进制数中 “1” 的个数，将这些结果返回为一个数组。


## 版本1

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

## 版本2

```
function countBit(n){    
  var ret = 0;    
  while(n > 0){
    ret += n & 1;
    n >>= 1;
  }    
  return ret;
}
```

## 版本3

```
function countBit(n){    
  var ret = 0;    
  while(n > 0){
    ret++;
    n &= n - 1;
  }    
  return ret;
}
```

## 版本4

```
function countBits(nums){    
  var ret = [0];    
  for(var i = 1; i <= nums; i++){
    ret.push(ret[i & i - 1] + 1);
  }    
  return ret;
}
```