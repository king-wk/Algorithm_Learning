## 剑指 Offer 47. 礼物的最大价值
在一个 m * n 的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值（价值大于 0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向右或者向下移动一格、直到到达棋盘的右下角。给定一个棋盘及其上面的礼物的价值，请计算你最多能拿到多少价值的礼物？

来源：[力扣](https://leetcode-cn.com/problems/li-wu-de-zui-da-jie-zhi-lcof)

题解：
```C++
class Solution {
public:
    int maxValue(vector<vector<int>>& grid) {
        if(grid.size() == 0 || grid[0].size() == 0)return 0;
        int m = grid.size(), n = grid[0].size();
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(!i && !j)continue;
                if(!i && j)grid[i][j] += grid[i][j - 1];
                else if(i && !j)grid[i][j] += grid[i - 1][j];
                else grid[i][j] += max(grid[i][j - 1], grid[i - 1][j]);
            }
        }
        return grid[m - 1][n - 1];
    }
};
```
