## 剑指 Offer 58 - I. 翻转单词顺序
输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。为简单起见，标点符号和普通字母一样处理。例如输入字符串"I am a student. "，则输出"student. a am I"。

来源：[力扣](https://leetcode-cn.com/problems/fan-zhuan-dan-ci-shun-xu-lcof)

题解：
```C++
class Solution {
public:
    string reverseWords(string s) {
        string res = "";
        int i = s.length() - 1, j = s.length() - 1;
        if(i < 0)return res;
        while(1){
            while(j >= 0 && s[j] == ' ')j--;
            i = j;
            while(i >= 0 && s[i] != ' ')i--;
            if(i >= -1 && i < j){
                res += s.substr(i + 1, j - i);
                res += " ";
            }
            j = i;
            if(i < 0)break;
        }
        return res.substr(0, res.length() - 1);
    }
};
```
