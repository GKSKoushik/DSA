TC : O(n) + O(n)  SC : O(3)
```cpp
class Solution {
public:
    int totalFruit(vector<int>& fruits) {
        int l = 0, r = 0, maxlen = 0;
        map<int,int> mpp;
        while(r < fruits.size()){
            mpp[fruits[r]]++;
            if(mpp.size() > 2){
                while(mpp.size() > 2){
                    mpp[fruits[l]]--;
                    if(mpp[fruits[l]] == 0){
                        mpp.erase(fruits[l]);
                    }
                    l++;
                }
            }
            if(mpp.size() <= 2){
                maxlen = max(maxlen , r-l+1);
            }
            r++;
        }
        return maxlen;
    }
};
```
TC:O(n)  SC:O(1)
```cpp
class Solution {
public:
    int totalFruit(vector<int>& fruits) {
        int l = 0, r = 0, maxlen = 0;
        map<int,int> mpp;
        while(r < fruits.size()) {
            mpp[fruits[r]]++;
            if(mpp.size() > 2){
                mpp[fruits[l]]--;
                if(mpp[fruits[l]] == 0){
                    mpp.erase(fruits[l]);
                }
                l++;
            }
            if(mpp.size() <= 2){
                maxlen = max(maxlen,r-l+1);
            }
            r++;

        }
        return maxlen;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/fruit-into-baskets/)
- [Striver-Video](https://www.youtube.com/watch?v=e3bs0uA1NhQ)
