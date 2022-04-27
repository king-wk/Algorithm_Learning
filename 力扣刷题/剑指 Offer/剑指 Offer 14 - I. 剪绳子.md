## 剑指 Offer 14 - I. 剪绳子
给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0], k[1]...k[m-1] 。请问 k[0] * k[1] *...* k[m-1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

来源：[力扣](https://leetcode-cn.com/problems/jian-sheng-zi-lcof)

题解：
```C++
class Solution {
public:
    int cuttingRope(int n) {
        vector<int> dp(n + 1, 0);
        dp[1] = 1;
        for(int i = 1; i <= n; i++){
            for(int j = i - 1; j > 0; j--){
                dp[i] = max(max(dp[i], (i - j) * j), (i - j) * dp[j]);
            }
        }
        return dp[n];
    }
};
```
