## 剑指 Offer 63. 股票的最大利润
假设把某股票的价格按照时间先后顺序存储在数组中，请问买卖该股票一次可能获得的最大利润是多少？

来源：[力扣](https://leetcode-cn.com/problems/gu-piao-de-zui-da-li-run-lcof/)

题解：
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int res = 0;
        if(prices.size() == 0)return res;
        int low = prices[0];
        for(int i = 1; i < prices.size(); i++){
            low = min(low, prices[i]);
            res = max(res, prices[i] - low);
        }
        return res;
    }
};
```
