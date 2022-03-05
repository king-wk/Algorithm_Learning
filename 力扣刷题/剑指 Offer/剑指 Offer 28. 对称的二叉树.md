## 剑指 Offer 28. 对称的二叉树
请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

来源：[力扣](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)

题解：
```C++
class Solution {
public:
    bool isSame(TreeNode* a, TreeNode* b) {
        if(a == NULL && b == NULL)return true;
        else if(a == NULL || b == NULL || a->val != b->val)return false;
        return isSame(a->left, b->right) && isSame(a->right, b->left);
    }
    bool isSymmetric(TreeNode* root) {
        if(root == NULL)return true;
        return isSame(root->left, root->right);
    }
};
```
