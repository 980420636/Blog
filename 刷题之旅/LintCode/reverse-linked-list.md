# 翻转链表

------

## 描述

> 翻转一个链表

## 样例

给出一个链表 **1->2->3->null**，这个翻转后的链表为 **3->2->1->null**

## 挑战

在原地一次翻转完成

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">链表</span> <span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">优步</span> <span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">脸书</span>

## 我的 C++ 代码

```cpp
/**
 * Definition of ListNode
 * 
 * class ListNode {
 * public:
 *     int val;
 *     ListNode *next;
 * 
 *     ListNode(int val) {
 *         this->val = val;
 *         this->next = NULL;
 *     }
 * }
 */


class Solution {
public:
    /*
     * @param head: n
     * @return: The new head of reversed linked list.
     */
    ListNode * reverse(ListNode * head) {
        // write your code here
        ListNode *next=NULL, *previous=NULL;
        while (head){
            previous=head->next;
            head->next=next;
            next=head;
            head=previous;
        }
        return next;
    }
};
```

