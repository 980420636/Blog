# 尾部的零

------

## 描述

> * 设计一个算法，计算出n阶乘中尾部零的个数

## 样例

<span style="color:red;font-weight:bold">11! = 39916800</span>，因此应该返回 2

## 挑战

O(logN)的时间复杂度

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">数学</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param n: A long integer
     * @return: An integer, denote the number of trailing zeros in n!
     */
    long long trailingZeros(long long n) {
        // write your code here, try to do it without arithmetic operators.
        long long count5=0;
        while (n>=5){
            count5+=n/=5;
        }
        return count5;
    }
};
```

