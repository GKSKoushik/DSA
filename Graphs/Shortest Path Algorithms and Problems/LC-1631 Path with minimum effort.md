- TC : O(E logV)
- SC : O(n * m)
```cpp
class Solution {
public:
    int minimumEffortPath(vector<vector<int>>& heights) {
        int n = heights.size();
        int m = heights[0].size();
        priority_queue<pair<int, pair<int, int>>, vector<pair<int, pair<int, int>>>, 
        greater<pair<int, pair<int, int>>>> pq;
        vector<vector<int>> dist(n, vector<int>(m, 1e9));
        dist[0][0] = 0;
        pq.push({0, {0, 0}});
        int dr[] = {-1, 0 ,1, 0};
        int dc[] = {0, 1, 0, -1};

        while(!pq.empty()){
            auto it = pq.top();
            pq.pop();
            int dis = it.first;
            int row = it.second.first;
            int col = it.second.second;
            if(row == n-1 && col == m-1) return dis;
            for(int i = 0; i < 4; i++){
                int nrow = row + dr[i];
                int ncol = col + dc[i];
                if(nrow >= 0 && nrow < n && ncol >=0 && ncol < m){
                    int eff = max(abs(heights[row][col] - heights[nrow][ncol]), dis);
                    if(eff < dist[nrow][ncol]){
                        dist[nrow][ncol] = eff;
                        pq.push({eff, {nrow, ncol}});
                    }
                }
            }
        }
        return -1;
    }
};
```
### Question : (For better understanding goto Leetcode or Striver Video as this question feels bit tipcal to expalain here)
- We are give a matrix of numbers we need to find minimum path with minimum effort to reach destination
- So there we be multiple paths to reach destination we need to find a path with minimum effort
- We can travel in only 4 directions up, down, left, right diagonals are not allowed
### Explaination :
- So here we take a priority queue to store the effort and the row and col , we use a 2D array to store the effort
- We always pick maximum effort of each path ans we chose minimum effort from all paths by using priority queue
- On the destination row and col to poped the we get the minimum effort as priroity queue is in min heap
### Reference :
- [LeetCode-Problem](https://leetcode.com/problems/path-with-minimum-effort/)
- [Striver-Video](https://www.youtube.com/watch?v=0ytpZyiZFhA)







