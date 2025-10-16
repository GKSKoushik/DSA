`SC : O(n*m)` `TC : O(n*m)` 
```cpp
class Solution {
  private:
    void dfs(vector<vector<int>> &vis, vector<vector<char>> &grid, int x, int y, int n, int m){
        vis[x][y] = 1;
        queue<pair<int, int>> q;
        q.push({x, y});
        
        int delrow[] = {-1,-1,0,1,1,1,0,-1};
        int delcol[] = {0,1,1,1,0,-1,-1,-1};
        while(!q.empty()){
            int row = q.front().first;
            int col = q.front().second;
            q.pop();
            for(int i = 0; i < 8; i++){
                int nrow = row + delrow[i];
                int ncol = col + delcol[i];
                if(nrow >= 0 && nrow < n && ncol >=0 && ncol < m && grid[nrow][ncol] == 'L' && !vis[nrow][ncol]){
                    vis[nrow][ncol] = 1;
                    q.push({nrow, ncol});
                }
            }
        }
        
    }
  public:
    int countIslands(vector<vector<char>>& grid) {
        // Code here
        int n = grid.size();
        int m = grid[0].size();
        int cnt = 0;
        vector<vector<int>> vis(n, vector<int>(m, 0));
        for(int i = 0; i < n; i++){
            for(int j = 0; j <m; j++){
                if(!vis[i][j] && grid[i][j] == 'L'){
                    dfs(vis, grid,  i, j, n, m);
                    cnt++;
                    
                }
            }
        }
        return cnt;
    }
};
```
Reference :
- [GFG-Problem](https://www.geeksforgeeks.org/problems/find-the-number-of-islands/1)
- [Striver-Video](https://www.youtube.com/watch?v=muncqlKJrH0)




