### Memoization
```cpp
class Solution {
public:
    int f(int idx, vector<int> &nums, vector<int> &dp){
        if(idx == 0) return nums[idx];
        if(idx < 0) return 0;

        if(dp[idx] != -1) return dp[idx];
        
        int pick = nums[idx] + f(idx - 2, nums, dp);
        int notpick = 0 + f(idx - 1, nums, dp);
        return dp[idx] = max(pick, notpick);
    }
    int rob(vector<int>& nums) {
        int size = nums.size();
        vector<int> dp(size ,-1);
        return f(size - 1, nums, dp);
    }
};
```
### Explaination:
 - Its a pick and not pick 
 - Check for not valid idx and 0 idx 
 - Using memoixation we store recurssion tree

- [LeetCode-Problem](https://leetcode.com/problems/house-robber/)
- [Striver-Video](https://www.youtube.com/watch?v=GrMBfJNk_NY)
