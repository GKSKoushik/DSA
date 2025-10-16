`SC : O(2n)` `TC : O(v+E)` 
```cpp
class Solution {
  private:
  bool dfs(int node, vector<int> &vis, vector<int> &path, vector<vector<int>> &adj){
      vis[node] = 1;
      path[node] = 1;
      
      for(auto it : adj[node]){
          if(!vis[it]){
              if(dfs(it, vis, path, adj) == true) return true;
          }
          else if(path[it]){
              return true;
          }
      }
      path[node] = 0;
      return false;
  }
  public:
    bool isCyclic(int V, vector<vector<int>> &edges) {
        // code here
        vector<vector<int>> adj(V);
        for(auto &edge : edges){
            int u = edge[0];
            int v = edge[1];
            
            adj[u].push_back(v);
        }
        vector<int> vis(V,0);
        vector<int> path(V,0);
        
        for(int i = 0; i < V; i++ ){
            if(!vis[i]){
                if(dfs(i, vis, path, adj) == true) return true;
            }
        }
        return false;
    }
};
```
Reference:
- [GFG-Problem](https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1)
- [Striver-Video](https://www.youtube.com/watch?v=9twcmtQj4DU)



