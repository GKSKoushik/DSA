`SC : O(n*m)` `TC : O(n*m)`
```cpp
class Solution {
public:
    vector<vector<int>> updateMatrix(vector<vector<int>>& mat) {
        int n = mat.size();
        int m = mat[0].size();
        vector<vector<int>> vis(n, vector<int>(m , 0));
        vector<vector<int>> dist(n, vector<int>(m,0));
        queue<pair<pair<int,int>,int>> q;
        for(int i = 0; i < n; i++ ){
            for(int j = 0; j < m; j++ ){
                if(!mat[i][j]){
                    q.push({{i, j}, 0});
                    vis[i][j] = 1;
                }
                else{
                    vis[i][j] = 0;
                }
            }
        }
        int delrow[] = {-1, 0, 1, 0};
        int delcol[] = {0, 1, 0, -1};
        while(!q.empty()){
            int row = q.front().first.first;
            int col = q.front().first.second;
            int steps = q.front().second;
            q.pop();
            dist[row][col] = steps;
            for(int i = 0; i < 4; i++){
                int crow = delrow[i] + row;
                int ccol = delcol[i] + col;
                if(crow >= 0 && crow < n && ccol >= 0 && ccol < m && vis[crow][ccol] == 0){
                    vis[crow][ccol] = 1;
                    q.push({{crow, ccol}, steps+1});
                }  
            }
        }
        return dist;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/01-matrix/)
- [Striver-Video](https://www.youtube.com/watch?v=edXdVwkYHF8)


