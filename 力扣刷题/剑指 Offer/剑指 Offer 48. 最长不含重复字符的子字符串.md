## 剑指 Offer 48. 最长不含重复字符的子字符串
请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。

来源：[力扣](https://leetcode-cn.com/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/)

题解：
```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char, int>data;
        int left = 0, res = 0;
        for(int i = 0; i < s.length(); i++){
            if(data.find(s[i]) != data.end()){
                left = max(left, data[s[i]] + 1);
            }
            res = max(res, i - left + 1);
            data[s[i]] = i;
        }
        return res;
    }
};
```
