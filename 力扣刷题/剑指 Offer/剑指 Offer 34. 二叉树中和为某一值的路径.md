## 剑指 Offer 34. 二叉树中和为某一值的路径
给你二叉树的根节点 root 和一个整数目标和 targetSum ，找出所有 从根节点到叶子节点 路径总和等于给定目标和的路径。

叶子节点 是指没有子节点的节点。

来源：[力扣](https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof)

题解：
```C++
class Solution {
public:
    void dfs(vector<vector<int>>& res, vector<int>& path, TreeNode* root, int target){
        if(root == nullptr)return;
        path.push_back(root->val);
        if(root->left == nullptr && root->right == nullptr && target == root->val)res.push_back(path);
        dfs(res, path, root->left, target - root->val);
        dfs(res, path, root->right, target - root->val);
        path.pop_back();
    }
    vector<vector<int>> pathSum(TreeNode* root, int target) {
        vector<vector<int>> res;
        vector<int> path;
        dfs(res, path, root, target);
        return res;
    }
};
```
