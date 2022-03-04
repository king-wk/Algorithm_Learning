## 剑指 Offer 32 - II. 从上到下打印二叉树 II
从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

来源：[力扣](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

题解：
```C++
// 法一：
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> res;
        if(root == NULL)return res;
        queue<TreeNode*> data;
        data.push(root);
        while(!data.empty()){
            int n = data.size();
            vector<int> level;
            for(int i = 0; i < n; i++){
                TreeNode* temp = data.front();
                data.pop();
                level.push_back(temp->val);
                if(temp->left)data.push(temp->left);
                if(temp->right)data.push(temp->right);
            }
            res.push_back(level);
        }
        return res;
    }
};
```
```C++
// 法二：将每一层的节点通过null隔开
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> res;
        if(root == NULL)return res;
        queue<TreeNode*> data;
        data.push(root);
        data.push(NULL);
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
            res.push_back(level);
        }
        return res;
    }
};
```
