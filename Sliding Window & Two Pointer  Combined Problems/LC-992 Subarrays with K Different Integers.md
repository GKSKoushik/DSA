TC : O(2n) SC : O(n)
```cpp
class Solution {
public:
    int f(vector<int>& nums, int k) {
        if(k < 0 ) return 0;
        int l = 0, r =0, maxlen = 0, cnt = 0;
        map<int,int> mpp;
        while(r < nums.size()){
            mpp[nums[r]]++;
            while(mpp.size() > k){
                mpp[nums[l]]--;
                if(mpp[nums[l]] ==0 ) mpp.erase(nums[l]);
                l++;
            }
            cnt = cnt + r - l + 1;
            r++;
        }
        return cnt;
    }
    int subarraysWithKDistinct(vector<int>& nums, int k){
        return f(nums , k) - f (nums, k - 1);
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/subarrays-with-k-different-integers/description/)
- [Striver-Video](https://www.youtube.com/watch?v=7wYGbV_LsX4)
