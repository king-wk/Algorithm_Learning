## 剑指 Offer 13. 机器人的运动范围
地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

来源：[力扣](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof)

题解：
```C++
class Solution {
public:
    bool calc_bitsum(int x, int y, int k){
        int res = 0;
        while(x){
            res += x % 10;
            x = x / 10;
        }
        while(y){
            res += y % 10;
            y = y / 10;
        }
        if(res > k)return false;
        return true;
    }
    int dfs(vector<vector<int>>& visit, int x, int y, int m, int n, int k){
        if(x < 0 || y < 0 || x >= m || y >= n || visit[x][y] || !calc_bitsum(x, y, k))return 0;
        visit[x][y] = 1;
        return 1 + dfs(visit, x + 1, y, m, n, k) + dfs(visit, x, y + 1, m, n, k);
    }
    int movingCount(int m, int n, int k) {
        vector<vector<int>> visit(m, vector<int>(n, 0));
        return dfs(visit, 0, 0, m, n, k);
    }
};
```
