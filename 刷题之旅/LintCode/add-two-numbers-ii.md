# 链表求和 II

------

## 描述

> 假定用一个链表表示两个数，其中每个节点仅包含一个数字。假设这两个数的数字 **顺序** 排列，请设计一种方法将两个数相加，并将其结果表现为链表的形式。

## 样例

给出 **6->1->7** + **2->9->5**。即，**617 + 295**。

返回 **9->1->2**。即，**912**。

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">链表</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">高精度</span>

## 我的 C++ 代码

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */


class Solution {
public:
    /*
     * @param l1: The first list.
     * @param l2: The second list.
     * @return: the sum list of l1 and l2.
     */
    ListNode * addLists2(ListNode * l1, ListNode * l2) {
        // write your code here
        int sum=0;
        stack<int> s1, s2;
        ListNode *result=NULL, *newNode=NULL;
        while (l1){
            s1.push(l1->val);
            l1=l1->next;
        }
        while (l2){
            s2.push(l2->val);
            l2=l2->next;
        }
        while (s1.size() || s2.size()){
            sum+=(s1.size() ? s1.top() : 0) + (s2.size() ? s2.top() : 0);
            newNode=new ListNode(sum%10);
            sum/=10;
            newNode->next=result;
            result=newNode;
            if (s1.size()) s1.pop();
            if (s2.size()) s2.pop();
        }
        if (sum){
            newNode=new ListNode(sum);
            newNode->next=result;
            result=newNode;
        }
        return result;
    }
};
```

