# 字符串查找

------

## 描述

> 对于一个给定的 source 字符串和一个 target 字符串，你应该在 source 字符串中找出 target 字符串出现的第一个位置(从0开始)。如果不存在，则返回 -1。

## 说明

> 在面试中我是否需要实现KMP算法？  
不需要，当这种问题出现在面试中时，面试官很可能只是想要测试一下你的基础应用能力。当然你需要先跟面试官确认清楚要怎么实现这个题。

## 样例

如果 source = **"source"** 和 target = **"target"**，返回 **-1**。

如果 source = **"abcdabcdefg"** 和 target = **"bcd"**，返回 **1**。

## 挑战

O(n^2)的算法是可以接受的。如果你能用O(n)的算法做出来那更加好。（提示：KMP）

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">基本实现</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">字符串处理</span> <span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">脸书</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param source: source string to be scanned.
     * @param target: target string containing the sequence of characters to match
     * @return: a index to the first occurrence of target in source, or -1  if target is not part of source.
     */
    int strStr(const char *source, const char *target) {
        // write your code here
        int i=0, j=0, k=0;
    	vector<int> next;
    	if (!source || !target) return -1;
    	getNext(target, next);
    	while (1){
    		while (source[k]!=0 && target[j]!=0 && source[k]==target[j]){
    			++k;
    			++j;
    		}
    		if (target[j]==0)
    			return i;
    		if (source[k]==0)
    			return -1;
    		if (j==0)
    			i=k=i+1;
    		else
    			i=k-(j=next[j]);
    	}
    }
    
    void getNext(const char *target, vector<int> &next){
    	int i=0, j=0;
    	for (; i<2; ++i){
    		if (target[i]!=0)
    			next.push_back(0);
    		else
    			return;
    	}
    	while (target[i]!=0){
    		while (j>0 && target[j]!=target[i-1]) j=next[j];
    		if (target[j]==target[i-1])
    			next.push_back(++j);
    		else
    			next.push_back(0);
    		++i;
    	}
    }
};
```

