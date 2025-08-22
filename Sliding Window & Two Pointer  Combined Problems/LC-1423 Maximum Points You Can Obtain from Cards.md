TC : O(n) SC : O(1)
```cpp
class Solution {
public:
    int maxScore(vector<int>& cardPoints, int k) {
        int lsum = 0 , rsum = 0, maxsum = 0;
        for(int  i = 0; i < k;i++){
            lsum = lsum + cardPoints[i];
        }
        maxsum = lsum;
        int r = cardPoints.size()-1;
        for(int i = k-1; i >= 0 ;i--){
            lsum = lsum - cardPoints[i];
            rsum = rsum + cardPoints[r];
            r--;
            maxsum = max(maxsum , lsum+rsum);
        }
        return maxsum;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)
- [Striver-Video](https://www.youtube.com/watch?v=pBWCOCS636U)

