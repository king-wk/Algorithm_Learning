## 剑指 Offer 54. 二叉搜索树的第k大节点
给定一棵二叉搜索树，请找出其中第 k 大的节点的值。

来源：[力扣](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

题解：
```C++
class Solution {
public:
    int kthLargest(TreeNode* root, int k) {
        if(root == NULL)return -1;
        stack<TreeNode*> st;
        int count = 0;
        while(root || !st.empty()){
            if(root){
                st.push(root);
                root = root->right;
            }else{
                root = st.top();
                st.pop();
                count++;
                if(count == k)return root->val;
                root = root->left;
            }
        }
        return -1;
    }
};
```
