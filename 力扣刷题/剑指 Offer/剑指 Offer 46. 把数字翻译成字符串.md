## 剑指 Offer 46. 把数字翻译成字符串
给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。

来源：[力扣](https://leetcode-cn.com/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof)

题解：
```C++
class Solution {
public:
    int translateNum(int num) {
        string s = to_string(num);
        int a = 0, b = 0, res = 1;
        for(int i = 0; i < s.length(); i++){
            a = b;
            b = res;
            res = b;
            if(i == 0)continue;
            if((s[i] <= '5' && s[i - 1] == '2') || s[i - 1] == '1')res += a;
        }
        return res;
    }
};
```
