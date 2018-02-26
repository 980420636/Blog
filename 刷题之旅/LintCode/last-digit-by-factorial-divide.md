# 阶乘除法的最后一位数

------

## 描述

> 给出两个数 **A** 和 **B**, 其中 **B >= A**. 我们需要计算结果 F 的最后一位数是什么, 其中F = **B! / A!**(1 <= A, B <= **10^18**, A 和 B 非常大)

## 样例

给出 A = 2, B = 4, 返回 2  
A! = 2 以及 B! = 24, F = 24 / 2 = 12 --> 最后一位数为 2

给出 A = 107, B = 109, 返回 2

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">数学</span><span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">谷歌</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param : the given number
     * @param : another number
     * @return: the last digit of B! / A! 
     */
    int computeLastDigit(long long A, long long B) {
        // write your code here
        int i, last, num=1;
        if (B-A>=5) return 0;
        for (i=B-A,last=(A+1)%10; i>0; --i){
            num*=last++;
            num%=10;
        }
        return num;
    }
};
```

