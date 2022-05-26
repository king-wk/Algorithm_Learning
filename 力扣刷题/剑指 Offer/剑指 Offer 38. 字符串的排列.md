## 剑指 Offer 38. 字符串的排列
输入一个字符串，打印出该字符串中字符的所有排列。
你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

来源：[力扣](https://leetcode.cn/problems/zi-fu-chuan-de-pai-lie-lcof/)

题解：
```C++
class Solution {
public:
    void dfs(string s, vector<string>& res, int k){
        if(k == s.length()){
            res.push_back(s);
            return;
        }
        set<char> data;
        for(int i = k; i < s.length(); i++){
            if(data.find(s[i]) != data.end())continue;
            data.insert(s[i]);
            swap(s[i], s[k]);
            dfs(s, res, k + 1);
            swap(s[i], s[k]);
        }
    }

    vector<string> permutation(string s) {
        vector<string> res;
        dfs(s, res, 0);
        return res;
    }
};
```
