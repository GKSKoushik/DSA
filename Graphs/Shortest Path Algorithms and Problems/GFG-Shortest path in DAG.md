- TC : O(V + E) + O(V + E)  For topo sort and for dist vector
- SC : O(V + E)
```cpp
class Solution {
  private:
    void topo(int node, stack<int>& st, vector<int>& vis, vector<vector<pair<int, int>>> adj){
        vis[node] = 1;
        for(auto& it : adj[node]){
            int v = it.first; 
            if(!vis[v]){
                topo(v, st, vis, adj);
            }
        }
        st.push(node);
    } 
  public:
    vector<int> shortestPath(int V, int E, vector<vector<int>>& edges) {
        // code here
        vector<vector<pair<int,int>>> adj(V);
        for(int i =0 ; i < E; i++){
            int v = edges[i][0];
            int u = edges[i][1];
            int wt = edges[i][2];
            
            adj[v].push_back({u, wt});
            
        }
        stack<int> st;
        vector<int> vis(V, 0);
        for(int i = 0; i < V; i++){
            if(!vis[i]){
                topo(i, st, vis, adj);
            }
        }
        vector<int> dist(V, 1e9);
        dist[0] = 0;
        while(!st.empty()){
            int node = st.top();
            st.pop();
            for(auto& it : adj[node]){
                int v = it.first;
                int wt = it.second;
                if(dist[node] + wt < dist[v]){
                    dist[v] = dist[node] + wt;
                }
            }
            
        }
        for(auto& it : dist){
            if(it == 1e9) it = -1;
        }
        return dist;
        
        
        
    }
};
```cpp

### Question :
 - Find shortest path in DAG
### Explaination
 - We use topo sort to get the stack of DAG order
 - By using the stack we fill the weights int distance vector
 - Not this process it strictly recomended of DAG as topo don't support for cyclic graph. To achieve this poblem we use dijkstra's Algorithm
### Reference :
- [GFG-Problem](https://www.geeksforgeeks.org/problems/shortest-path-in-undirected-graph/1)
- [Striver-Video](https://www.youtube.com/watch?v=ZUFQfFaU-8U&list=PLgUwDviBIf0oE3gA41TKO2H5bHpPd7fzn&index=28)





