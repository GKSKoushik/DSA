- `TC : O(n)`
- `SC : O(n)`
```cpp
class Solution {
public:
    int f(int i,int j,vector<vector<int>> &mat, vector<vector<int>> &dp){
        if(i >= 0 && j >=0 && mat[i][j] == 1) return 0;

        if(i == 0 && j == 0) return 1;
        if(i < 0 || j < 0) return 0;

        //if(mat[i][j] == 1) return 0; I can simply write this too
        //if(i == 0 && j == 0) return 1;

        if(dp[i][j] != -1) return dp[i][j];
        int up = f(i-1, j, mat, dp);      // moves upwards
        int sd = f(i, j-1, mat, dp);      // moves sidewards

        return dp[i][j] = up+sd;
    }
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size();
        int n = obstacleGrid[0].size();

        vector<vector<int>> dp(m, vector<int>(n, -1));

        return f(m-1, n-1, obstacleGrid, dp);
    }
};
```
### Question 
- Number of possible ways to reach destination
- If path is (0, 0) to (m-1, n-1) we need to find number of diffrent ways to reach the destination
- If matrix[i][j] = 1 then we should treat it as obstacle and we should choose other path
### Explaination
- We check for all possible ways in 2D array 
- Base cases are if we reach destination we return 1, If we reach out of bounds we return 0
- We add one more case here if matrix[i][j] = 1 then we return 0 
### Reference;
- [LeetCode-Problem](https://leetcode.com/problems/unique-paths-ii/)
- [Striver-Video](https://www.youtube.com/watch?v=TmhpgXScLyY)
