## 剑指 Offer 57 - II. 和为s的连续正数序列
输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

来源：[力扣](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof)

题解：
```C++
class Solution {
public:
    vector<vector<int>> findContinuousSequence(int target) {
        vector<vector<int>> res;
        for(int l = 1, r = 2; l < r;){
            int sum = (l + r) * (r - l + 1) / 2;
            if(sum == target){
                vector<int> subres;
                for(int i = l; i <= r; i++)subres.push_back(i);
                res.push_back(subres);
                l++;
            }else if(sum > target)l++;
            else r++;
        }
        return res;
    }
};
```
