```cpp
class Solution {
  public:
    bool isCyclic(int V, vector<vector<int>> &edges) {
        // code here
        vector<vector<int>> adj(V);
        for(auto &edge : edges){
            int u = edge[0];
            int v = edge[1];
            
            adj[u].push_back(v);
        }
        
        vector<int> indeg(V);
        queue<int> q;
        for(int i = 0 ; i < V; i++){
            for(auto it : adj[i]){
                indeg[it]++;
            }
        }
        
        for(int i = 0 ; i < V; i++){
            if(indeg[i] == 0){
                q.push(i);
            }
        }
        
        int cnt = 0;
        while(!q.empty()){
            int node = q.front();
            q.pop();
            cnt++;
            
            for(auto it : adj[node]){
                indeg[it]--;
                if(indeg[it] == 0){
                    q.push(it);
                }
            }
        }
        if(cnt == V) return false;
        return true;
    }
};
```
Reference:
- [GFG-Problem](https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1)
- [Striver-Video](https://www.youtube.com/watch?v=iTBaI90lpDQ)
