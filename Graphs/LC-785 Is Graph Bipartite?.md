`SC : O(v)` `TC : O(v+2E)`
```cpp
class Solution {
private:
    bool dfs(int node, int col, vector<int> &color, vector<vector<int>> &adj){
        color[node] = col;

        for(auto it : adj[node]){
            if(color[it] == -1){
                if(dfs(it, !col, color, adj) == false) return false;
            }
            else if(color[it] == col) return false;
        }
        return true;
    }
public:
    bool isBipartite(vector<vector<int>>& graph) {
        int V = graph.size();

        vector<int> color(V, -1);
        for(int i = 0; i < V; i++){
            if(color[i] == -1){
                if(dfs(i, 0, color, graph) == false) return false;
            }
        }
        return true;
    }
};
```
Refrence:
- [LeetCode-Problem](https://leetcode.com/problems/is-graph-bipartite/)
- [Striver-Video](https://www.youtube.com/watch?v=KG5YFfR0j8A)
