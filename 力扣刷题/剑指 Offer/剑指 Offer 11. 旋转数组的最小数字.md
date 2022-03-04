## 剑指 Offer 11. 旋转数组的最小数字
把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。
给你一个可能存在 重复 元素值的数组 numbers ，它原来是一个升序排列的数组，并按上述情形进行了一次旋转。请返回旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一次旋转，该数组的最小值为1。  

来源：[力扣](https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof)

题解：
```C++
class Solution {
public:
    int min_binary(vector<int>& numbers, int left, int right) {
        if(left == right) return numbers[left];
        int mid = (left + right) / 2;
        int minv = min_binary(numbers, left, mid);
        if(mid + 1 <= right)minv = min(minv, min_binary(numbers, mid + 1, right));
        return minv;
    }
    int minArray(vector<int>& numbers) {
        return min_binary(numbers, 0, numbers.size() - 1);
    }
};
```
