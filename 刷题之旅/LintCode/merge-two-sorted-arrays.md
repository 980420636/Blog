# 合并排序数组 II

------

## 描述

> * 合并两个排序的整数数组A和B变成一个新的数组。

## 样例

给出A=<span style="color:red;font-weight:bold">[1,2,3,4]</span>，B=<span style="color:red;font-weight:bold">[2,4,5,6]</span>，返回<span style="color:red;font-weight:bold">[1,2,2,3,4,4,5,6]</span>

## 挑战

你能否优化你的算法，如果其中一个数组很大而另一个数组很小？

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">数组</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">排序数组</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param A: sorted integer array A
     * @param B: sorted integer array B
     * @return: A new sorted integer array
     */
    vector<int> mergeSortedArray(vector<int> &A, vector<int> &B) {
        // write your code here
        int indexA=A.size()-1, indexB=B.size()-1, indexC=A.size()+B.size();
    	vector<int> C(indexC--);
    	while (indexC>=0){
    		if (indexA>=0){
    			if (indexB>=0){
    				C[indexC--]=A[indexA]>B[indexB] ? A[indexA--] : B[indexB--];
    			}
    			else{
    				C[indexC--]=A[indexA--];
    			}
    		}
    		else{
    			C[indexC--]=B[indexB--];
    		}
    	}
    	return C;
    }
};
```

