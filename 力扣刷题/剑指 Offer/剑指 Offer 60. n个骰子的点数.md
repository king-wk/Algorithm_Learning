## 剑指 Offer 60. n个骰子的点数
把n个骰子扔在地上，所有骰子朝上一面的点数之和为s。输入n，打印出s的所有可能的值出现的概率。

你需要用一个浮点数数组返回答案，其中第 i 个元素代表这 n 个骰子所能掷出的点数集合中第 i 小的那个的概率。

来源：[力扣](https://leetcode.cn/problems/nge-tou-zi-de-dian-shu-lcof)

题解：
```C++
class Solution {
public:
    vector<double> dicesProbability(int n) {
        vector<double>res(5 * n + 1, 0);
        vector<vector<double>>dp(n + 1, vector<double>(6 * n + 1, 0));
        for(int i = 1; i <= 6; i++)dp[1][i] = 1.0 / 6.0;
        for(int i = 2; i <= n; i++){
            for(int j = i; j <= 6 * i; j++){
                for(int k = 1; k <= 6; k++){
                    if(j > k)dp[i][j] += dp[i - 1][j - k] * 1.0 / 6.0;
                    else break;
                }
            }
        }
        for(int i = 0; i < 5 * n + 1; i++)res[i] = dp[n][n + i];
        return res;
    }
};
```
