
`SC : O(n*l)` <span style="color: orange;"><i>Typically O(n)</i></span> <br>
`TC : O(n*l*26) ` <span style="color: orange;"><i>n = number of words in word list, l = length of each word</i></span> 
```cpp
class Solution {
public:
    int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
        queue<pair<string, int>> q;
        q.push({beginWord, 1});
        unordered_set<string> st(wordList.begin(), wordList.end());
        st.erase(beginWord);

        while(!q.empty()){
            string word = q.front().first;
            int steps = q.front().second;
            q.pop();
            
            if(endWord == word) return steps; 
            for(int i = 0; i < word.size(); i++){
                char original = word[i];
                for(char ch= 'a'; ch <= 'z'; ch++){
                    word[i] = ch;
                    if(st.find(word) != st.end()){
                        st.erase(word);
                        q.push({word, steps + 1});
                    }
                }
                word[i] = original;

            }
        }
        return 0;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/word-ladder/)
- [Striver-Video](https://www.youtube.com/watch?v=tRPda0rcf8E)
