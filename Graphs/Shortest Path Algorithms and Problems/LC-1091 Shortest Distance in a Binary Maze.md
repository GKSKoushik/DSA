- TC : O(n * m)
- SC : O(n * m)
```cpp
class Solution {
public:
    int shortestPathBinaryMatrix(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        if(grid[0][0] == 1 || grid[n-1][m-1] == 1) return -1;
        vector<vector<int>> vis(n, vector<int>(m, 1e9));
        vis[0][0] = 1;
        queue<pair<int,pair<int, int>>> q;
        q.push({1,{0,0}});
        while(!q.empty()){
            auto it = q.front();
            q.pop();
            int dis = it.first;
            int r = it.second.first;
            int c = it.second.second;
            if(n-1 == r && m-1 == c) return dis;
            for(int i = -1; i < 2 ; i++){
                for(int j = -1; j < 2; j++){
                    if(i == 0 && j == 0) continue;
                    int cr = r + i;
                    int cc = c + j;
                    if(cr >= 0 && cr < n && cc >= 0 && cc < m && grid[cr][cc] == 0 && dis + 1 < vis[cr][cc]){
                        vis[cr][cc] = dis + 1;
                        q.push({dis + 1,{cr,cc}});
                    }
                }
            }
            
        }
        return - 1;
    }
};
```
### Question :
 - We start from "grid[0][0]" and we end in "grid[row-end][col-end]" we travel throught node if node is equal to 0
 - We need to find shortest 0 path from start to end if there is no path exists we return -1
### Explaination :
 - Note : We wont count the moves we count the node so we start initial weight and vis[0][0] as 1
 - We do BFS traversal by checking vis matrix as it hold the distance 
### Reference : 
 - [LeetCode-Problem](https://www.youtube.com/watch?v=U5Mw4eyUmw4&list=PLgUwDviBIf0oE3gA41TKO2H5bHpPd7fzn&index=37)
 - [Striver-Video](https://leetcode.com/problems/shortest-path-in-binary-matrix/)



