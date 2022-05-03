## 剑指 Offer 55 - II. 平衡二叉树
输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树。

来源：[力扣](https://leetcode-cn.com/problems/ping-heng-er-cha-shu-lcof/)

题解：
```C++
class Solution {
public:
    int Depth(TreeNode* root){
        if(root == NULL)return 0;
        int ld = Depth(root->left);
        int rd = Depth(root->right);
        if(ld == -1 || rd == -1 || abs(ld - rd) > 1){
            return -1;
        }
        return max(ld, rd) + 1;
    }
    bool isBalanced(TreeNode* root) {
        if(Depth(root) == -1){
            return false;
        }
        return true;
    }
};
```
