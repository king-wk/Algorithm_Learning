## 剑指 Offer 55 - I. 二叉树的深度
输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。

来源：[力扣](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/)

题解：
```C++
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root == NULL)return 0;
        else return 1 + max(maxDepth(root->left), maxDepth(root->right));
    }
};
```
