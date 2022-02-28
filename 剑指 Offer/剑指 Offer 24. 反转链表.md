## 剑指 Offer 24. 反转链表
定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

来源：[力扣](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)

题解：
```C++
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(head == NULL)return NULL;
        ListNode* pre = NULL;
        ListNode* curr = head;
        while(curr){
            ListNode* next = curr->next;
            curr->next = pre;
            pre = curr;
            curr = next;
        }
        return pre;
    }
};
```
