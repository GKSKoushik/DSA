- `TC : O(n * m)`
- `SC : O(n * m) + O (path_length)  path_length = (m-1) + (n - 1)`
```cpp
class Solution {
public:
    int f(int i, int j, vector<vector<int>> &grid, vector<vector<int>> &dp){
        if(i == 0 && j == 0) return grid[0][0];
        if(i < 0 || j < 0) return 1e9;

        if(dp[i][j] != -1) return dp[i][j];
        int up = grid[i][j] + f(i - 1, j, grid, dp);
        int sd = grid[i][j] + f(i, j - 1, grid, dp);

        return dp[i][j] = min(up, sd);
    }
    int minPathSum(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();

        vector<vector<int>> dp(m, vector<int>(n, -1));
    
        return f(m - 1, n - 1, grid, dp);
    }
};
```
### Question 
- Number of possible ways to reach destination
- If path is (0, 0) to (m-1, n-1) we need to find number of diffrent ways to reach the destination with minimum value
### Explaination
- We check for all possible ways in 2D array 
- Base cases are if we reach destination we return grid[0][0], If we reach out of bounds we return 1e9 to always choose min value
### Reference
- [LeetCode-Problem](https://leetcode.com/problems/minimum-path-sum/)
- [Striver-Video](https://www.youtube.com/watch?v=_rgTlyky1uQ)
