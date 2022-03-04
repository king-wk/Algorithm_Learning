## 剑指 Offer 03. 数组中重复的数字
找出数组中重复的数字。在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

来源：[力扣](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof)

题解：
```C++
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        int n = nums.size();
        vector<bool>data(n, false);
        for(int i = 0; i < n; i++){
            if(data[nums[i]] == 0)data[nums[i]] = 1;
            else return nums[i];
        }
        return -1;
    }
};
```
