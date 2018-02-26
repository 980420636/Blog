# 交叉字符串

------

## 描述

> 给出三个字符串:s1、s2、s3，判断s3是否由s1和s2交叉构成。

## 样例

比如 s1 = **"aabcc"** s2 = **"dbbca"**  
&ensp;&ensp;&ensp;&ensp;- 当 s3 = **"aadbbcbcac"**，返回 true.  
&ensp;&ensp;&ensp;&ensp;- 当 s3 = **"aadbbbaccc"**， 返回 false.

## 挑战

要求时间复杂度为O(n^2)或者更好

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">最长公共子串</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">动态规划</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param s1: A string
     * @param s2: A string
     * @param s3: A string
     * @return: Determine whether s3 is formed by interleaving of s1 and s2
     */
    bool isInterleave(string &s1, string &s2, string &s3) {
        // write your code here
        return _isInterleave(s3, s1, s2, 0, 0, 0) 
            || _isInterleave(s3, s2, s1, 0, 0, 0);
    }
    
    bool _isInterleave(string &target, string &main, string &slave, int iTarget, int iMain, int iSlave){
    	if (iTarget==target.length())
    		return true;
    	if (target[iTarget]==main[iMain]){
    		++iTarget;
    		++iMain;
    		return _isInterleave(target, main, slave, iTarget, iMain, iSlave) 
    		    || _isInterleave(target, slave, main, iTarget, iSlave, iMain);
    	}
    	else{
    		return false;
    	}
    }
};
```

