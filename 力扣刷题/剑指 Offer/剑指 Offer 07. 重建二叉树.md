## 剑指 Offer 07. 重建二叉树
输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。

假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

来源：[力扣](https://leetcode-cn.com/problems/zhong-jian-er-cha-shu-lcof/)

题解：
```C++
class Solution {
public:
    void restructTree(vector<int>& preorder, vector<int>& inorder, int start, int end, int r, TreeNode*& root) {
        if(start > end)root = NULL;
        else {
            int i = start;
            while(i <= end && inorder[i] != preorder[r])i++;
            root = new TreeNode(preorder[r]);
            restructTree(preorder, inorder, start, i - 1, r + 1, root->left);
            restructTree(preorder, inorder, i + 1, end, r + i - start + 1, root->right);
        }
    }
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        TreeNode* root = NULL;
        restructTree(preorder, inorder, 0, preorder.size() - 1, 0, root);
        return root;
    }
};
```
