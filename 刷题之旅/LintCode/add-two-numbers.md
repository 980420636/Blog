# 链表求和

------

## 描述

> 你有两个用链表代表的整数，其中每个节点包含一个数字。数字存储按照在原来整数中 **相反** 的顺序，使得第一个数字位于链表的开头。写出一个函数将两个整数相加，用链表形式返回和。

## 样例

给出两个链表 **3->1->5->null** 和 **5->9->2->null**，返回 **8->0->8->null**

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">链表</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">Cracking The Coding Interview</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">高精度</span>

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
     * @param l1: the first list
     * @param l2: the second list
     * @return: the sum list of l1 and l2 
     */
    ListNode * addLists(ListNode * l1, ListNode * l2) {
        // write your code here
        int sum=0;
        ListNode *result=NULL, *newNode=NULL;
        while (l1 || l2){
            sum+=(l1 ? l1->val : 0) + (l2 ? l2->val : 0);
            if (result){
                newNode->next=new ListNode(sum%10);
                newNode=newNode->next;
            }
            else{
                result=newNode=new ListNode(sum%10);
            }
            sum/=10;
            if (l1) l1=l1->next;
            if (l2) l2=l2->next;
        }
        if (sum){
            newNode->next=new ListNode(sum);
        }
        return result;
    }
};
```

