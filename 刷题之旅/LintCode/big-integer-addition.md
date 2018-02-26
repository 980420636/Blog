# 大整数加法

------

## 描述

> * 以字符串的形式给出两个非负整数 **num1** 和 **num2**，返回 **num1** 和 **num2** 的和。
> * 注意事项
>     * num1 和 num2 的长度都小于5100。
>     * num1 和 num2 都只包含数字 0-9。
>     * num1 和 num2 都不包含任何前导零。
>     * 您不能使用任何内置的BigInteger库内的方法或直接将输入转换为整数。

## 样例

给定 num1 = **"123"**，num2 = **"45"**

返回 **"168"**

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">数学</span> <span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">爱彼迎</span> <span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">谷歌</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param num1: a non-negative integers
     * @param num2: a non-negative integers
     * @return: return sum of num1 and num2
     */
    string addStrings(string &num1, string &num2) {
        // write your code here
        int sum=0;
        string result="";
        int i1=num1.length()-1, i2=num2.length()-1;
        while (i1>=0 || i2>=0){
            sum+=(i1>=0 ? num1[i1]-48 : 0) + (i2>=0 ? num2[i2]-48 : 0);
            result=(char)(sum%10+48)+result;
            sum/=10;
            if (i1>=0) --i1;
            if (i2>=0) --i2;
        }
        if (sum){
            result=(char)(sum+48)+result;
        }
        return result;
    }
};
```

