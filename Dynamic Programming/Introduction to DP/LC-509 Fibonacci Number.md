### Memoization
- `SC : O(n) + O(n)`
- `TC : O(n)`
```cpp
class Solution {
public:
    int fib(int n) {
        vector<int> dp(n+1, -1);
        return helper(n , dp);
    }
    int helper(int n, vector<int>& dp){
        if(n <= 1) return n;
        if(dp[n] != -1) return dp[n];
        return dp[n] = helper(n-1, dp)+helper(n-2, dp);
    }
};
```
### Tabulation
 - `SC : O(1)`
 - `TC : O(n)`
```cpp
class Solution {
public:
    int fib(int n) {
        int prev1 = 1;
        int prev2 = 0;
        for(int i = 2; i <= n; i++){
            int curi = 0;
            curi = prev1 + prev2;
            prev2 = prev1;
            prev1 = curi;
        }
        return prev1;
    }
};
```


Reference:
 - [LeetCode-Problem](https://leetcode.com/problems/fibonacci-number/description/)
 - [Striver-Video](http://youtube.com/watch?v=tyB0ztf0DNY)
