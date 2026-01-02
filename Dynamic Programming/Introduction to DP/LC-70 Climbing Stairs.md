### Memoization 
 - `TC : O(n)`
 - `SC : O(n)`
```cpp
class Solution {
public:
    int climbStairs(int n) {
        vector<int> dp(n+1,-1);
        return helper(dp , n);
        
    }
    int helper(vector<int> &dp, int n){
        if(n <= 1) return 1;
        if(dp[n] != -1){
            return dp[n];
        }
        return dp[n] = helper(dp, n-1) + helper(dp, n-2);
    }
};
```
### Tabulation
 - `SC : O(1)`
 - `TC : O(n)`
```cpp
class Solution {
public:
    int climbStairs(int n) {
        if(n <= 1) return 1;
        int prev2 = 1;
        int prev1 = 1;
        for(int i = 2; i <= n; i++){
            int curr = prev2 + prev1;
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }
};
```


Reference:
 - [LeetCode-Problem](https://leetcode.com/problems/climbing-stairs/)
 - [Strievr-Video](https://www.youtube.com/watch?v=mLfjzJsN8us)
