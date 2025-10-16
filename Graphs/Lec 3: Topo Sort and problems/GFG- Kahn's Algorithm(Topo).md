```cpp
class Solution {
  public:
    vector<int> topoSort(int V, vector<vector<int>>& edges) {
        // code here
        vector<vector<int>> adj(V);
        
        for(auto &edge : edges){
            int u = edge[0];
            int v = edge[1];
            
            adj[u].push_back(v);
        }
        
        vector<int> indeg(V);
        
        for(int i = 0; i < V ; i++){
            for(auto it : adj[i]){
                indeg[it]++;
            }
        }
        
        queue<int> q;
        for(int i = 0 ; i < V; i++){
            if(indeg[i] == 0){
                q.push(i);
            }
        }
        
        vector<int> topo;
        while(!q.empty()){
            int node = q.front();
            q.pop();
            topo.push_back(node);
            
            for(auto it : adj[node]){
                indeg[it]--;
                if(indeg[it] == 0) q.push(it);
            }
        }
        return topo;
    }
};
```
Reference:
- [GFG-Problem](https://www.youtube.com/watch?v=73sneFXuTEg)
- [Striver-Video](https://www.youtube.com/watch?v=73sneFXuTEg)
