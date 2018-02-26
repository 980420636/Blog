# 二叉查找树中搜索区间

------

## 描述

> 给定两个值 k1 和 k2（k1 < k2）和一个二叉查找树的根节点。找到树中所有值在 k1 到 k2 范围内的节点。即打印所有x (k1 <= x <= k2) 其中 x 是二叉查找树的中的节点值。返回所有升序的节点值。

## 样例

如果有 k1 = **10** 和 k2 = **22**, 你的程序应该返回 **[12, 20, 22]**.
>&ensp;&ensp;&ensp;&ensp;20  
&ensp;&ensp;&ensp;/&ensp;&ensp;\  
&ensp;&ensp;8&ensp;&ensp;&ensp;22  
&ensp;/&ensp;\  
4&ensp;&ensp;&ensp;12

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">二叉查找树</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">二叉树</span>

## 我的 C++ 代码

```cpp
/**
 * Definition of TreeNode:
 * class TreeNode {
 * public:
 *     int val;
 *     TreeNode *left, *right;
 *     TreeNode(int val) {
 *         this->val = val;
 *         this->left = this->right = NULL;
 *     }
 * }
 */


class Solution {
public:
    /*
     * @param root: param root: The root of the binary search tree
     * @param k1: An integer
     * @param k2: An integer
     * @return: return: Return all keys that k1<=key<=k2 in ascending order
     */
    vector<int> searchRange(TreeNode * root, int k1, int k2) {
        // write your code here
        vector<int> vec;
    	searchRangeFillVector(vec, root, k1, k2);
    	return vec;
    }
    
    void searchRangeFillVector(vector<int> &vec, TreeNode * root, int k1, int k2){
    	vector<int>::iterator iter;
    	if (!root) return;
    	if (root->val>=k1){
    	    searchRangeFillVector(vec, root->left, k1, k2);
    	    if (root->val<=k2){
    	        vec.push_back(root->val);
    	        searchRangeFillVector(vec, root->right, k1, k2);
    	    }
    	}
    	else{
    	    searchRangeFillVector(vec, root->right, k1, k2);
    	}
    }
};
```

