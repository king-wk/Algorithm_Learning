## 剑指 Offer 53 - I. 在排序数组中查找数字 I
统计一个数字在排序数组中出现的次数。

来源：[力扣](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

题解：
```C++
class Solution {
public:
    int search_in_vector(vector<int>& nums, int left, int right, int target) {
        if(left > right || nums[right] < target)return 0;
        if(left == right)return nums[left] == target;
        int mid = (left + right) / 2;
        return search_in_vector(nums, left, mid, target) + search_in_vector(nums, mid + 1, right, target);

    }
    int search(vector<int>& nums, int target) {
        return search_in_vector(nums, 0, nums.size() - 1, target);
    }
};
```
