## 剑指 Offer 52. 两个链表的第一个公共节点
输入两个链表，找出它们的第一个公共节点。

来源：[力扣](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

题解：
```C++
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* h1 = headA;
        ListNode* h2 = headB;
        int n1 = 0, n2 = 0;
        while(h1){
            n1++;
            h1 = h1->next;
        }
        while(h2){
            n2++;
            h2 = h2->next;
        }
        while(n1 != n2){
            if(n1 > n2){
                n1--;
                headA = headA->next;
            }else{
                n2--;
                headB = headB->next;
            }
        }
        while(n1){
            if(headA == headB)return headA;
            headA = headA->next;
            headB = headB->next;
            n1--;
        }
        return NULL;
    }
};
```
