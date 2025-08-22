TC : O(2*2n) SC : O(1)
```cpp
class Solution {
public:
    int f(vector<int> nums, int goal){
        if(goal < 0 ) return 0;
        int l = 0, r = 0, cnt = 0,sum = 0;
        while(nums.size() > r){
            sum = sum + nums[r];
            while(sum > goal){
                sum = sum - nums[l];
                l++;
            }
            cnt = cnt + r - l + 1;
            r++;
        }
        return cnt;
    }

    int numSubarraysWithSum(vector<int>& nums, int goal) {
        return f(nums,goal)-f(nums,goal-1);
    }
};
```cpp
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/binary-subarrays-with-sum/)
- [Striver-Video](https://www.youtube.com/watch?v=XnMdNUkX6VM)
