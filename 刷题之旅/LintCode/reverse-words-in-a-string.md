# 翻转字符串

------

## 描述

> * 给定一个字符串，逐个翻转字符串中的每个单词。

## 说明

> * 单词的构成：无空格字母构成一个单词
> * 输入字符串是否包括前导或者尾随空格？可以包括，但是反转后的字符不能包括
> * 如何处理两个单词间的多个空格？在反转字符串中间空格减少到只含一个

## 样例

给出字符串 **"hello world"**，返回 **"world hello"**

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">字符串处理</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param s: A string
     * @return: A string
     */
    string reverseWords(string &s) {
        // write your code here
        int start, end, isFirst=1, i;
        string result="";
        end=s.length()-1;
        while (1){
            while (end>=0 && s[end]==' ') --end;
            if (end<0) break;
            start=end-1;
            while (start>=0 && s[start]!=' ') --start;
            if (isFirst){
                isFirst=0;
            }
            else{
                result+=' ';
            }
            for (i=start+1; i<=end; ++i){
                result+=s[i];
            }
            end=start-1;
        }
        return result;
    }
};
```

