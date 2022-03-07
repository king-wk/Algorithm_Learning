## 剑指 Offer 42. 连续子数组的最大和
输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。
要求时间复杂度为O(n)。

来源：[力扣](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

题解：
```C++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int res = nums[0], sum = nums[0];
        for(int i = 1; i < nums.size(); i++){
            if(sum <= 0){
                res = max(res, sum);
                sum = nums[i];
            }else sum += nums[i];
            res = max(res, sum);
        }
        return res;
    }
};
```
