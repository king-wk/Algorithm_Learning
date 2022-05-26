## 剑指 Offer 49. 丑数
我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。

来源：[力扣](https://leetcode.cn/problems/chou-shu-lcof/)

题解：
```C++
class Solution {
public:
    int nthUglyNumber(int n) {
        int dp[n];
        int a = 0, b = 0, c = 0;
        dp[0] = 1;
        for(int i = 1; i < n; i++){
            int n1 = dp[a] * 2, n2 = dp[b] * 3, n3 = dp[c] * 5;
            dp[i] = min(n1, min(n2, n3));
            if(dp[i] == n1)a++;
            if(dp[i] == n2)b++;
            if(dp[i] == n3)c++;
        }
        return dp[n - 1];
    }
};
```
