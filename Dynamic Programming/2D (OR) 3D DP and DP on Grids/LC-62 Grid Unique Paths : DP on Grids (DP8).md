- `TC : O(n)`
- `SC : O(n)`
```cpp
class Solution {
public:
    int f(int i , int j, vector<vector<int>> &dp){
        if(i == 0 && j == 0) return 1;
        if(i < 0 || j < 0) return 0;

        if(dp[i][j] != -1) return dp[i][j];
        int up = f(i - 1, j, dp);
        int sd = f(i , j -1, dp);

        return dp[i][j] = up + sd;
    }
    int uniquePaths(int m, int n) {
        vector<vector<int>> dp(m , vector<int>(n , -1));
        return f(m-1 , n-1, dp);
    }
};
```
### Question 
- Number of possible ways to reach destination
- If path is (0, 0) to (m-1, n-1) we need to find number of diffrent ways to reach the destination
### Explaination
- We check for all possible ways in 2D array 
- Base cases are if we reach destination we return 1, If we reach out of bounds we return 0
### Reference
- [LeetCode-Problem](https://leetcode.com/problems/unique-paths/description/)
- [Striver-Video](https://www.youtube.com/watch?v=sdE0A2Oxofw)
