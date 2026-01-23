`SC : O(n*m) + O(n*m)` `TC : O(n*m)`
```cpp
class Solution {
private:
    void dfs(int inicolor, vector<vector<int>> &ans, vector<vector<int>> &image, int sr, int sc, int color){
        int n = image.size();
        int m = image[0].size();
        int drow[] = {-1,0,1,0};
        int dcol[] = {0,1,0,-1};
        ans[sr][sc] = color;
        for(int i = 0; i<4; i++ ){
            int row = sr + drow[i];
            int col = sc + dcol[i];
            if(row < n && col < m && row >=0 && col >=0 && ans[row][col] != color && image[row][col] == inicolor ){
                dfs(inicolor, ans, image, row, col, color);
            }
        }
    }
public:
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int iniColor = image[sr][sc];
        vector<vector<int>> ans = image;
        dfs(iniColor, ans, image, sr, sc, color); 
        return ans;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/flood-fill/)
- [Striver-Video](https://www.youtube.com/watch?v=C-2_uSRli8o)
