## 剑指 Offer 26. 树的子结构
输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)
B是A的子结构， 即 A中有出现和B相同的结构和节点值。

例如:
给定的树 A=[3, 4, 5, 1, 2]，给定的树 B=[4, 1]，返回 true，因为 B 与 A 的一个子树拥有相同的结构和节点值。

来源：[力扣](https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof)

题解：
```C++
class Solution {
public:
    bool isSub(TreeNode* A, TreeNode* B){
        if(B == NULL)return true;
        else if(A == NULL || A->val != B->val)return false;
        else return isSub(A->left, B->left) && isSub(A->right, B->right);
    }
    bool isSubStructure(TreeNode* A, TreeNode* B) {
        if(A == NULL || B == NULL)return false;
        if(isSub(A, B))return true;
        else return isSubStructure(A->left, B) || isSubStructure(A->right, B);
    }
};
```
