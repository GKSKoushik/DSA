TC : O(2n) + O(m)  SC : O(256)
```cpp
class Solution {
public:
    string minWindow(string s, string t) {
        int l = 0, r = 0, cnt = 0,sindex = -1;
        int  n = s.size(), m = t.size();
        int minlen = INT_MAX;
        int hash[256] = {0};
        for(int i = 0; i < m ;i++){
            hash[t[i]]++;
        }
        while(r < n){
            if(hash[s[r]] > 0) cnt++;
            hash[s[r]]--;
            while(m == cnt){
                if(r-l+1 < minlen){
                    minlen = r - l + 1;
                    sindex = l;
                }
                hash[s[l]]++;
                if(hash[s[l]] > 0) cnt--;
                l++;
            }
            r++;
        }
        return sindex==-1?"":s.substr(sindex,minlen);
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/minimum-window-substring/)
- [Striver-Video](https://www.youtube.com/watch?v=WJaij9ffOIY)
