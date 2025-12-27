`TC : V + 2E`  
```cpp
class Solution {
  public:
    vector<int> shortestPath(int V, vector<vector<int>> &edges, int src) {
        // code here
        vector<int> dist(V, INT_MAX);
        dist[src] = 0;
        vector<vector<int>> adj(V);
        for(auto &it : edges){
            adj[it[0]].push_back(it[1]);
            adj[it[1]].push_back(it[0]);
        }
        queue<int> q;
        q.push(src);
        while(!q.empty()){
            int node = q.front();
            q.pop();
            for(auto it : adj[node]){
                if(dist[node] + 1 < dist[it]){
                    dist[it]  = 1 + dist[node];   
                    q.push(it);
                }
            }
        }
        vector<int> ans(V, -1);
        for(int i = 0; i < V; i++){
            if(dist[i] != INT_MAX){
                ans[i] = dist[i];
            }
        }
        return ans;
    }
};  
```
Reference:
- [GFG-Problem](https://www.geeksforgeeks.org/problems/shortest-path-in-undirected-graph-having-unit-distance/1)
- [Striver-Video](https://www.youtube.com/watch?v=tRPda0rcf8E&list=PLgUwDviBIf0oE3gA41TKO2H5bHpPd7fzn&index=29)







