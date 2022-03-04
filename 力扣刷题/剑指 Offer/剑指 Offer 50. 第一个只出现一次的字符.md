## 剑指 Offer 50. 第一个只出现一次的字符
在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

来源：[力扣](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

题解：
```C++
class Solution {
public:
    char firstUniqChar(string s) {
        unordered_map<char, int>data;
        int k = 0;
        for(int i = 0; i < s.length(); i++){
            if(data.find(s[i]) != data.end())data[s[i]] = 0;
            else data[s[i]] = 1;
        }
        for(int i = 0; i < s.length(); i++){
            if(data[s[i]])return s[i];
        }
        return ' ';
    }
};
```
