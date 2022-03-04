## 剑指 Offer 53 - II. 0～n-1中缺失的数字
一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。

来源：[力扣](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof)

题解：
```C++
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int l = 0, r = nums.size() - 1;
        while(l <= r){
            int m = (l + r) / 2;
            if(nums[m] == m)l = m + 1;
            else r = m - 1;
        }
        return l;
    }
};
```
