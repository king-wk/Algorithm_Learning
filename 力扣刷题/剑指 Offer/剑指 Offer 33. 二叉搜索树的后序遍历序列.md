## 剑指 Offer 33. 二叉搜索树的后序遍历序列

输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 true，否则返回 false。假设输入的数组的任意两个数字都互不相同。

来源：[力扣](https://leetcode.cn/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)

题解：
```C++
class Solution {
public:
    bool verify(vector<int>& postorder, int root, int low){
        if(root <= low)return true;
        int i = low;
        while(i < root && postorder[i] < postorder[root])i++;
        int left = i - 1;
        while(i < root && postorder[i] > postorder[root])i++;
        return i == root && verify(postorder, left, low) && verify(postorder, root - 1, left + 1);
    }
    bool verifyPostorder(vector<int>& postorder) {
        return verify(postorder, postorder.size() - 1, 0);
    }
};
```
