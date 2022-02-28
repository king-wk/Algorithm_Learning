## 剑指 Offer 35. 复杂链表的复制
请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。

来源：[力扣](https://leetcode-cn.com/problems/fu-za-lian-biao-de-fu-zhi-lcof)

题解：
```C++
// 有随机指针，遍历复制可能出现随机指针指向的节点还没有复制
// 所以先遍历一次复制所有的节点，用hash表保存（原节点-复制节点）
// 以便在第二次遍历的时候能快速找到节点的 next 节点和 random 节点
class Solution {
public:
    Node* copyRandomList(Node* head) {
        Node* res = NULL;
        if(head == NULL)return res;
        unordered_map<Node*, Node*> hash_map;
        Node* curr = head;
        while(curr){
            Node* newnode = new Node(curr->val);
            hash_map[curr] = newnode;
            curr = curr->next;
        }
        curr = head;
        while(curr){
            hash_map[curr]->next = hash_map[curr->next];
            hash_map[curr]->random = hash_map[curr->random];
            curr = curr->next;
        }
        return hash_map[head];
    }
};
```
