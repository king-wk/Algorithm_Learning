## 剑指 Offer 16. 数值的整数次方
实现 pow(x, n) ，即计算 x 的 n 次幂函数（即，$$ x^n $$）。不得使用库函数，同时不需要考虑大数问题。

来源：[力扣](https://leetcode-cn.com/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

题解：
```C++
class Solution {
public:
    double myPow(double x, int n) {
        if(x == 0 || x == 1)return x;
        long long exp = n;
        if(exp < 0)exp = -exp, x = 1 / x;
        double res = 1.0;
        while(exp){
            if(exp % 2)res *= x;
            x *= x;
            exp /= 2;
        }
        return res;
    }
};
```
