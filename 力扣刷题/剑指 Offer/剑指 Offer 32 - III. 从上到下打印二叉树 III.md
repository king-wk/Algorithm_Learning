## 剑指 Offer 32 - III. 从上到下打印二叉树 III
请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

来源：[力扣](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

题解：
```C++
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> res;
        if(root == NULL)return res;
        queue<TreeNode*> data;
        data.push(root);
        data.push(NULL);
        int left = 0;
        while(!data.empty()){
            vector<int> level;
            while(data.front()){
                TreeNode* temp = data.front();
                data.pop();
                level.push_back(temp->val);
                if(temp->left)data.push(temp->left);
                if(temp->right)data.push(temp->right);
            }
            data.pop();
            if(!data.empty())data.push(NULL);
            if(left)reverse(level.begin(), level.end());
            res.push_back(level);
            left = 1 - left;
        }
        return res;
    }
};
```
