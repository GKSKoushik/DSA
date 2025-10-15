`SC : O(v)` `TC : O(v+2E)` 
```cpp
class Solution {
private:
    bool dfs(int node, int col, vector<int> &color, vector<vector<int>> &adj){
        color[node] = col;
        
        for(auto it : adj[node]){
            if(color[it] == -1){
                if(!dfs(it, !col, color, adj)) return false;
            }
            else if(color[it] == col) return false;
        }
        return true;
    }
    
public:
    bool isBipartite(int V, vector<vector<int>> &edges) {
        vector<vector<int>> adj(V);
        for(auto &edge : edges){
            int u = edge[0];
            int v = edge[1];
            adj[u].push_back(v);
            adj[v].push_back(u);
        }
        

        vector<int> color(V, -1);
        

        for(int i = 0; i < V; i++){
            if(color[i] == -1){
                if(!dfs(i, 0, color, adj)) return false;
            }
        }
        return true;
    }
};
```
Reference:
- [GFG-Problem](https://www.geeksforgeeks.org/problems/bipartite-graph/1#using-depthfirst-search-dfs)
- [Striver-Video](https://www.youtube.com/watch?v=KG5YFfR0j8A)
