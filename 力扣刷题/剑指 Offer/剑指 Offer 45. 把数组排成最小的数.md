## 剑指 Offer 45. 把数组排成最小的数
输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。

来源：[力扣](https://leetcode.cn/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

题解：
```C++
class Solution {
public:
    string minNumber(vector<int>& nums) {
        vector<string> data_str;
        for(int i = 0; i < nums.size(); i++)data_str.push_back(to_string(nums[i]));
        sort(data_str, 0, data_str.size() - 1);
        string res;
        for(int i = 0; i < data_str.size(); i++)res += data_str[i];
        return res;
    }
    void sort(vector<string>& data_str, int l, int r){
        if(l >= r)return;
        int i = l, j = r;
        while(i < j){
            while(i < j && data_str[j] + data_str[l] >= data_str[l] + data_str[j])j--;
            while(i < j && data_str[i] + data_str[l] <= data_str[l] + data_str[i])i++;
            if(i < j)swap(data_str[i], data_str[j]);
        }
        swap(data_str[j], data_str[l]);
        sort(data_str, l, i - 1);
        sort(data_str, i + 1, r);
    }
};
```
