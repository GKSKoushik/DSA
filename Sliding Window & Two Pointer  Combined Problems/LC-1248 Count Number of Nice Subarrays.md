TC : O(2 * 2n) SC : O(n)
```cpp
class Solution {
public:
    int f(vector<int> nums,int k){
        int l = 0, r = 0, sum = 0, cnt = 0;
        while(r < nums.size()){
            sum = sum + nums[r]%2;
            while(sum > k){
                sum = sum - nums[l]%2;
                l++;
            }
            cnt = cnt + r-l+1;
            r++;
        }
        return cnt;
    }
    int numberOfSubarrays(vector<int>& nums, int k) {
        return f(nums,k) - f(nums,k-1);
    }
};
```
