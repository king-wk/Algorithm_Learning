## 剑指 Offer 56 - I. 数组中数字出现的次数
一个整型数组 nums 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

来源：[力扣](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

题解：
```C++
class Solution {
public:
    vector<int> singleNumbers(vector<int>& nums) {
        vector<int> res;
        int dev = 1, n = 0;
        for(int i = 0; i < nums.size(); i++){
            n = n ^ nums[i];
        }
        while((dev & n) == 0){
            dev = dev << 1;
        }
        int a = 0, b = 0;
        for(int i = 0; i < nums.size(); i++){
            if(dev & nums[i]){
                a = a ^ nums[i];
            }else{
                b = b ^ nums[i];
            }
        }
        res.push_back(a);
        res.push_back(b);
        return res;
    }
};
```
