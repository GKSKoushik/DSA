```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        for(int i = 0 ; i < s.size();i++){
            if(s[i] == '(' || s[i] == '[' || s[i] == '{'){
                st.push(s[i]);
            }
            else {
                if(st.empty()) return false;
                char ch = st.top();
                st.pop();
                if(s[i] == ')' && ch != '(' ||
                   s[i] == '}' && ch != '{' ||
                   s[i] == ']' && ch != '['){
                    return false;
                }
            }
        }
        return st.empty();
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/valid-parentheses/description/)
- [Striver-Video](https://www.youtube.com/watch?v=xwjS0iZhw4I)
