## 剑指 Offer 65. 不用加减乘除做加法
写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“\*”、“/” 四则运算符号。

来源：[力扣](https://leetcode-cn.com/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)

题解：
```C++
class Solution {
public:
    int add(int a, int b) {
        return b == 0 ? a : add(a ^ b, (unsigned int)(a & b) << 1);
    }
};
```
