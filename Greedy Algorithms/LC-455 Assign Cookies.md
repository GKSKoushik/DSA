```cpp
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        int m = g.size(), n = s.size();
        sort(g.begin(),g.end());
        sort(s.begin(),s.end());
        int l = 0, r = 0;
        while(l < m && r < n){
            if(g[l] <= s[r]){
                l++;
            }
            r++;
        } 
        return l;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/assign-cookies/description/)
- [Striver-Video](https://www.youtube.com/watch?v=DIX2p7vb9co)
