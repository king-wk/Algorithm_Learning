## 剑指 Offer 18. 删除链表的节点
给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。
返回删除后的链表的头节点。

来源：[力扣](https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/)

题解：
```C++
class Solution {
public:
    ListNode* deleteNode(ListNode* head, int val) {
        if(head == NULL)return NULL;
        else if(head->val == val)return head->next;
        ListNode* pre = head;
        ListNode* p = head->next;
        while(p){
            if(p->val == val)pre->next = p->next;
            else pre = p;
            p = p->next;
        }
        return head;
    }
};
```
