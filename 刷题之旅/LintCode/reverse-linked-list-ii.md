# 翻转链表 II

------

## 描述

> * 翻转链表中第m个节点到第n个节点的部分
> * 注意事项
>     * m，n满足1 ≤ m ≤ n ≤ 链表长度

## 样例

给出链表 **1->2->3->4->5->null**， m = 2 和n = 4，返回 **1->4->3->2->5->null**

## 挑战

在原地一次翻转完成

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">链表</span>

## 我的 C++ 代码

```cpp
/**
 * Definition of singly-linked-list:
 * 
 * class ListNode {
 * public:
 *     int val;
 *     ListNode *next;
 *     ListNode(int val) {
 *        this->val = val;
 *        this->next = NULL;
 *     }
 * }
 */


class Solution {
public:
    /*
     * @param head: ListNode head is the head of the linked list 
     * @param m: An integer
     * @param n: An integer
     * @return: The head of the reversed ListNode
     */
    ListNode * reverseBetween(ListNode * head, int m, int n) {
        // write your code here
        int i;
        ListNode *cur=head, *beforeStart=NULL, *end=NULL, *next=NULL, *previous=NULL;
        if (m>1){
            for (i=2; i<m; ++i){
                cur=cur->next;
            }
            beforeStart=cur;
            cur=cur->next;
        }
        end=cur;
        for (i=m; i<=n; ++i){
            previous=cur->next;
            cur->next=next;
            next=cur;
            cur=previous;
        }
        end->next=cur;
        if (m>1){
            beforeStart->next=next;
        }
        else{
            head=next;
        }
        return head;
    }
};
```

