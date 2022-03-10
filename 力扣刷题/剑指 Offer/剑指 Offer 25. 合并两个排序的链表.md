## 剑指 Offer 25. 合并两个排序的链表
输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。

来源：[力扣](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

题解：
```C++
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* newhead = new ListNode(-1);
        ListNode* curr = newhead;
        while(l1 || l2){
            if(!l1 || (l2 && l1->val >= l2->val)){
                curr->next = l2;
                l2 = l2->next;
            }else{
                curr->next = l1;
                l1 = l1->next;
            }
            curr = curr->next;
        }
        return newhead->next;
    }
};
```
