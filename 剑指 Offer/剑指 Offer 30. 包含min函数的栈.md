## 剑指 Offer 30. 包含min函数的栈
定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

来源：[力扣](https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/)

题解：
```C++
class MinStack {
    stack<int> minstack;
public:
    /** initialize your data structure here. */
    MinStack() {
        while(!minstack.empty())minstack.pop();
    }
    
    void push(int x) {
        if(minstack.empty()){
            minstack.push(x);
            minstack.push(x);
        }else{
            int minx = std::min(x, minstack.top());
            minstack.push(x);
            minstack.push(minx);
        }
    }
    
    void pop() {
        minstack.pop();
        minstack.pop();
    }
    
    int top() {
        if(minstack.empty())return -1;
        int minx = minstack.top();
        minstack.pop();
        int topx = minstack.top();
        minstack.push(minx);
        return topx;
    }
    
    int min() {
        if(minstack.empty())return -1;
        return minstack.top();
    }
};
```
