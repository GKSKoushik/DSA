`SC : O(n*m)` `TC : O(n*m)`
```cpp
class Solution {
private:
    void dfs(vector<vector<int>> &vis, vector<vector<char>> &board, int row, int col){
        int n = board.size();
        int m = board[0].size();
        vis[row][col] = 1;

        int nrow[] = {-1, 0, 1, 0};
        int ncol[] = {0, 1, 0, -1};
        for(int i = 0; i<4;i++ ){
            int rrow = row + nrow[i];
            int rcol = col + ncol[i];
            if(rrow >= 0 && rrow < n && rcol >= 0 && rcol < m && !vis[rrow][rcol] && board[rrow][rcol] == 'O'){
                dfs(vis, board, rrow, rcol);

            }
        }

    }
public:
    void solve(vector<vector<char>>& board) {
        int n = board.size();
        int m = board[0].size();
        vector<vector<int>> vis(n, vector<int>(m, 0));
        for(int j = 0 ; j < m; j++){
            if(!vis[0][j] && board[0][j] == 'O'){
                dfs(vis, board , 0 , j);
            }
            if(!vis[n-1][j] && board[n-1][j] == 'O'){
                dfs(vis, board, n-1, j);
            }
        }
        for(int i = 0 ; i < n; i++){
            if(!vis[i][0] && board[i][0] == 'O'){
                dfs(vis , board, i , 0);
            }
            if(!vis[i][m-1] && board[i][m-1] == 'O'){
                dfs(vis, board, i, m-1);
            }
        }
        for(int i = 0 ; i < n; i++){
            for(int j = 0; j < m; j++){
                if(!vis[i][j] && board[i][j] == 'O'){
                    board[i][j] = 'X';
                }
            }
        }
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/surrounded-regions/description/)
- [Striver-Video](https://www.youtube.com/watch?v=BtdgAys4yMk)
