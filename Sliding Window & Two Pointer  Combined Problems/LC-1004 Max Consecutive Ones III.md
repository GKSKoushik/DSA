This is Better approch \
TC:O(n)+O(n)   SC:O(1)
```cpp
class Solution {
public:
    int longestOnes(vector<int>& nums, int k) {
        int l = 0 , r = 0 , maxlen = 0 , zero =0;
        while(r<nums.size()){
            if(nums[r] == 0) zero++;
            while(zero>k){
                if(nums[l] == 0) {
                    zero--;
                }
                l++;
            }
            if(zero <=k ) {
                int len = r-l+1;
                maxlen = max(maxlen,len);
            }
            r++;
        }
        return maxlen;
        
    }
};
```
This is Optimal approach \
TC:O(n)   SC:O(1)
```cpp
class Solution {
public:
    int longestOnes(vector<int>& nums, int k) {
        int l = 0 , r = 0 , maxlen = 0 , zero =0;
        while(r<nums.size()) {
            if(nums[r] == 0) zero++;
            if(zero > k) {
                if(nums[l] == 0) zero--;
                l++;
            }
            if(zero <= k) {
                int len = r-l+1;
                maxlen = max(maxlen,len);
            }
            r++;
        }
        return maxlen;        
    }
};
```
Reference:
- [LeetCode](https://leetcode.com/problems/max-consecutive-ones-iii/submissions/1741556077/)
- [Striver-Video](https://www.youtube.com/watch?v=3E4JBHSLpYk)
