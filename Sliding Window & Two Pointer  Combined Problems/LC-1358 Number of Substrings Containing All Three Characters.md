TC : O(n) SC : O(1)
```cpp
class Solution {
public:
    int numberOfSubstrings(string s) {
        int cnt = 0;
        int lastseen[3] = {-1,-1,-1};
        for(int i = 0; i < s.size();i++){
            lastseen[s[i]-'a'] = i;
            if(lastseen[0] != -1 && lastseen[0] != -1 && lastseen[1] != -1 && lastseen[2] != -1){
                cnt = cnt + (1 + min(lastseen[0],min(lastseen[1], lastseen[2])));
            }
        }
        return cnt;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/description/)
- [Striver-Video](https://www.youtube.com/watch?v=xtqN4qlgr8s)
