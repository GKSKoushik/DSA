### Memoization
```cpp
class Solution {
public:
    int f(vector<int> &nums, int idx, vector<int> &dp){
        if(idx == 0) return nums[idx];
        if(idx < 0) return 0;
        
        if(dp[idx] != -1) return dp[idx];

        int pick = nums[idx] + f(nums, idx - 2, dp);
        int notpick = 0 + f(nums, idx - 1, dp);

        return dp[idx] = max(pick, notpick);
    }
    int rob(vector<int>& nums) {
        int size = nums.size();
        vector<int> temp1, temp2;
        if(size == 0) return 0;
        if(size == 1) return nums[0];

        for(int i = 0 ; i  < size; i++){
            if(i != 0 ) temp1.push_back(nums[i]);
            if(i != size-1) temp2.push_back(nums[i]);
        }
        vector<int> dp1(temp1.size() ,  - 1), dp2(temp2.size(), -1);
        return max(f(temp1, temp1.size()-1 , dp1) , f(temp2, temp2.size()-1, dp2));
    }
};
```
### Explaination:
- Same pick and not pick but here its a circular array so
- We take array a 2 diffent arrays they are 0 to size-1 and 1 to size then we check max from both arrays and return 
- [LeetCode-Problem](https://leetcode.com/problems/house-robber-ii/submissions/1894630339/)
- [Striver-Video](https://www.youtube.com/watch?v=3WaxQMELSkw)
