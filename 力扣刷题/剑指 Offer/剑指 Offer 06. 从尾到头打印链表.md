## 剑指 Offer 06. 从尾到头打印链表
输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

来源：[力扣](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

题解：

```C++
// 法一：
class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        vector<int> res;
        if(head == NULL)return res;
        int num = 0;
        while(head){
            res.push_back(head->val);
            head = head->next;
            num++;
        }
        int i = 0, j = num - 1;
        while(i < j){
            int temp = res[i];
            res[i] = res[j];
            res[j] = temp;
            i++;
            j--;
        }
        return res;
    }
};
```

```C++
// 法二：递归
class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        vector<int> res;
        if(head == NULL)return res;
        res = reversePrint(head->next);
        res.push_back(head->val);
        return res;
    }
};
```
