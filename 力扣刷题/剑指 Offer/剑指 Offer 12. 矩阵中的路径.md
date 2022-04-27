## 剑指 Offer 12. 矩阵中的路径
给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false 。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

来源：[力扣](https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof)

题解：
```C++
class Solution {
public:
    int move[4][2] = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
    bool dfs(vector<vector<char>>& board, string word, int x, int y, int z){
        if(z == word.length())return true;
        if(x < 0 || y < 0 || x >= board.size() || y >= board[0].size() || board[x][y] != word[z])return false;
        board[x][y] = '0';
        for(int i = 0; i < 4; i++){
            int xi = x + move[i][0];
            int yi = y + move[i][1];
            if(dfs(board, word, xi, yi, z + 1))return true;
        }
        board[x][y] = word[z];
        return false;
    }
    bool exist(vector<vector<char>>& board, string word) {
        int n = board.size(), m = board[0].size();
        bool state = false;
        for(int i = 0; i < n; i++){
            for(int j = 0; j < m; j++){
                if(dfs(board, word, i, j, 0))return true;
            }
        }
        return false;
    }
};
```
