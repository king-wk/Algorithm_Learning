## 剑指 Offer 36. 二叉搜索树与双向链表
输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。

来源：[力扣](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)

题解：
```C++
class Solution {
    Node* pre = NULL;
    Node* head = NULL;
public:
    void dfs(Node* root){
        if(root == NULL)return;
        dfs(root->left);
        if(pre == NULL)head = root;
        else pre->right = root;
        root->left = pre;
        pre = root;
        dfs(root->right);
    }
    Node* treeToDoublyList(Node* root) {
        if(root == NULL)return root;
        dfs(root);
        head->left = pre;
        pre->right = head;
        return head;
    }
};
```
