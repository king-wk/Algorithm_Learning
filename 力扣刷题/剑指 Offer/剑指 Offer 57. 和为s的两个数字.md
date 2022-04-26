## 剑指 Offer 57. 和为s的两个数字
输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

来源：[力扣](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

题解：
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1;
        while(left < right){
            if(nums[left] + nums[right] < target)left++;
            else if(nums[left] + nums[right] > target)right--;
            else return vector<int>{nums[left], nums[right]};
        }
        return vector<int>{-1, -1};
    }
};
```
