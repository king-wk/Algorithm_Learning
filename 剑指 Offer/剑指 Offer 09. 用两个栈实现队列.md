## 剑指 Offer 09. 用两个栈实现队列
用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )

来源：[力扣](https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof)

题解：
```C++
class CQueue {
    stack<int> data1;
    stack<int> data2;
public:
    CQueue() {
        while(!data1.empty())data1.pop();
        while(!data2.empty())data2.pop();
    }
    
    void appendTail(int value) {
        data1.push(value);
    }
    
    int deleteHead() {
        int res = -1;
        if(data2.empty()){
            while(!data1.empty()){
                data2.push(data1.top());
                data1.pop();
            }
        }
        if(data2.empty())return res;
        res = data2.top();
        data2.pop();
        return res;
    }
};

```
