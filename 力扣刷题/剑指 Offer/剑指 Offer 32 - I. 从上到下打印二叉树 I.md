## 剑指 Offer 32 - I. 从上到下打印二叉树 I
从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。

来源：[力扣](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)

题解：
```C++
class Solution {
public:
    vector<int> levelOrder(TreeNode* root) {
        vector<int> res;
        if(root == NULL)return res;
        queue<TreeNode*> data;
        data.push(root);
        while(!data.empty()){
            TreeNode* temp = data.front();
            data.pop();
            res.push_back(temp->val);
            if(temp->left)data.push(temp->left);
            if(temp->right)data.push(temp->right);
        }
        return res;
    }
};
```
