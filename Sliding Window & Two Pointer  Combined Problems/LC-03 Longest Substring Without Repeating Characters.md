```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int hash[256];
        for (int i = 0 ; i < 256;i++){
            hash[i] = -1;
        }
        int n = s.size();
        int l = 0, r = 0, maxlen = 0;
        while(r < n){
            if(hash[s[r]] != -1){
                if(hash[s[r]] >= l){
                    l = hash[s[r]] + 1;
                }
            }
            int len = r - l + 1;
            maxlen = max(maxlen, len);

            hash[s[r]] = r;
            r++;
        }
        return maxlen;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- [Striver-Video](https://www.youtube.com/watch?v=-zSxTJkcdAo)
