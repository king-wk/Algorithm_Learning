## 剑指 Offer 04. 二维数组中的查找
在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

来源：[力扣](https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof)

题解：
```C++
class Solution {
public:
    bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) {
        if(matrix.size() == 0 || matrix[0].size() == 0)return false;
        int i = 0, j = matrix[0].size() - 1;
        while(i < matrix.size() && j >= 0){
            if(matrix[i][j] > target)j--;
            else if(matrix[i][j] < target)i++;
            else return true;
        }
        return false;
    }
};
```
