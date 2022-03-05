## 剑指 Offer 27. 二叉树的镜像
请完成一个函数，输入一个二叉树，该函数输出它的镜像。

例如输入：root = [4,2,7,1,3,6,9]，
镜像输出：[4,7,2,9,6,3,1]

来源：[力扣](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof)

题解：
```C++
class Solution {
public:
    TreeNode* mirrorTree(TreeNode* root) {
        if(root == NULL)return root;
        mirrorTree(root->left);
        mirrorTree(root->right);
        TreeNode* temp = root->left;
        root->left = root->right;
        root->right = temp;
        return root;
    }
};
```
