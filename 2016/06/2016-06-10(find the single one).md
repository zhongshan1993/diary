# find the single one #

这是一道简单的LeetCode题，主要思想是使用异或位操作，a^b^a = b, 原题题目如下：

Single Number.
Given an array of integers, every element appears twice except for one. Find that single one.
Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

我用javascript的解法如下

```
function singleNum(arr) {
    var result = 0;
    for (i in arr) {
        result ^= arr[i];
    }
    return result;
}
```
