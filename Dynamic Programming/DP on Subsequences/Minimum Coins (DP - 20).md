### Memoization
- TC : O(n * T)
- SC : O(n * T) + O(T)
```cpp
class Solution {
public:
    int f(int idx, int tar, vector<int>& nums, vector<vector<int>>& dp){
        if(idx == 0){
            if(tar % nums[0] == 0) return tar/nums[idx];
            else return 1e9;
        }
        if(dp[idx][tar] != -1) return dp[idx][tar];
        int nottake = 0 + f(idx - 1, tar, nums,dp);
        int take = 1e9;
        if(nums[idx] < tar){
            take = 1 + f(idx, tar - nums[idx], nums,dp);
        }
        return dp[idx][tar] = min(take, nottake);
    }
    int coinChange(vector<int>& coins, int amount) {
        vector<vector<int>> dp(coins.size(), vector<int>(amount + 1, -1));
        int ans = f(coins.size()-1, amount, coins, dp);
        if(ans >= 1e9){
            return -1;
        }
        return ans;
    }
};
```
### Tabulation
- TC : O(n * T);
- SC : O(n * T);
#### 2D dp approach
```cpp
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        int n = coins.size();
        vector<vector<int>> dp(n, vector<int>(amount + 1,0));
        for(int T = 0; T <= amount; T++){
            if(T % coins[0] == 0) dp[0][T] = T / coins[0];
            else dp[0][T] = 1e9;
        }
        for(int i = 1; i < n; i++){
            for(int T = 0; T <= amount; T++){
                int nottake = 0 + dp[i - 1][T];
                int take = 1e9;
                if(coins[i] <= T){
                    take = 1 + dp[i][T - coins[i]];
                }
                dp[i][T] = min(take, nottake); 
            }
        }
        int ans = dp[n - 1][amount];
        if(ans >= 1e9) return -1;
        return ans;
    }
}; 
```
