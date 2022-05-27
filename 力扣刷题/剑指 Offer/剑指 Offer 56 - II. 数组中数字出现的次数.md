## 剑指 Offer 56 - II. 数组中数字出现的次数
在一个数组 nums 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字。

来源：[力扣](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

题解：
```C++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int record[32];
        memset(record, 0, sizeof(record));
        for(int i = 0; i < nums.size(); i++){
            for(int j = 0; j < 32; j++){
                record[j] += nums[i] & 1;
                nums[i] = nums[i] >> 1;
            }
        }
        int res = 0;
        for(int i = 0; i < 32; i++){
            if(record[i] % 3 != 0)res += 1 << i;
        }
        return res;
    }
};
```
