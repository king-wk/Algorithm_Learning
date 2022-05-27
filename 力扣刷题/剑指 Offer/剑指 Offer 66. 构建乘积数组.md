## 剑指 Offer 66. 构建乘积数组
给定一个数组 A[0, 1, …, n-1]，请构建一个数组 B[0, 1, …, n-1]，其中 B[i] 的值是数组 A 中除了下标 i 以外的元素的积, 即 B[i]=A[0]×A[1]×…×A[i-1]×A[i+1]×…×A[n-1]。不能使用除法。

来源：[力扣](https://leetcode.cn/problems/gou-jian-cheng-ji-shu-zu-lcof)

题解：
```C++
class Solution {
public:
    vector<int> constructArr(vector<int>& a) {
        int n = a.size();
        vector<int> b(n, 0);
        int x = 1;
        for(int i = 0; i < n; i++){
            b[i] = x;
            x *= a[i];
        }
        x = 1;
        for(int i = n - 1; i >= 0; i--){
            b[i] *= x;
            x *= a[i];
        }
        return b;
    }
};
```
