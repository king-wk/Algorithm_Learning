## 剑指 Offer 05. 替换空格
请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

来源：[力扣]()

题解：
```C++
class Solution {
public:
    string replaceSpace(string s) {
        string res;
        int i = 0;
        while(i < s.length()) {
            if(s[i] == ' ') {
                res.append("%20");
            } else res.push_back(s[i]);
            i++;
        }
        return res;
    }
};
```
