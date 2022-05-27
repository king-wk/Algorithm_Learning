## 剑指 Offer 59 - II. 队列的最大值
请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。

若队列为空，pop_front 和 max_value 需要返回 -1

来源：[力扣](https://leetcode.cn/problems/dui-lie-de-zui-da-zhi-lcof)

题解：
```C++
class MaxQueue {
    queue<int> Q;
    deque<int> Max_Q;
public:
    MaxQueue() {

    }
    
    int max_value() {
        if(Q.empty())return -1;
        return Max_Q.front();
    }
    
    void push_back(int value) {
        Q.push(value);
        while(!Max_Q.empty() && Max_Q.back() < value){
            Max_Q.pop_back();
        }
        Max_Q.push_back(value);
    }
    
    int pop_front() {
        if(Q.empty())return -1;
        int value = Q.front();
        Q.pop();
        if(Max_Q.front() == value)Max_Q.pop_front();
        return value;
    }
};
```
