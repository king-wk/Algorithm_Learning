## 剑指 Offer 21. 调整数组顺序使奇数位于偶数前面
输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。

来源：[力扣](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

题解：
```C++
class Solution {
public:
    vector<int> exchange(vector<int>& nums) {
        int left = 0, right = nums.size() - 1;
        while(left < right){
            while(left < right && nums[left] % 2 == 1)left++;
            while(left < right && nums[right] % 2 == 0)right--;
            if(left < right)swap(nums[left], nums[right]);
        }
        return nums;
    }
};
```
