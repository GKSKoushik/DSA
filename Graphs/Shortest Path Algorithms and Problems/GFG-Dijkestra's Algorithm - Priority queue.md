TC : O(E logE)
SC : O(V + E)
```cpp
    class Solution {
      public:
        vector<int> dijkstra(int V, vector<vector<int>> &edges, int src) {
            // Code here
            vector<vector<pair<int, int>>> adj(V);
            int E = edges.size();
            for(int i = 0; i < E; i++){
                int u = edges[i][0];
                int v = edges[i][1];
                int wt = edges[i][2];
                adj[u].push_back({v, wt});
                adj[v].push_back({u, wt});
            }
            vector<int> dist(V, 1e9);
            priority_queue<pair<int, int> , vector<pair<int, int>>, greater<pair<int, int>>> pq;
            dist[src] = 0;
            pq.push({0, src});
            
            while(!pq.empty()){
                int dis = pq.top().first;
                int node = pq.top().second;
                pq.pop();
                if(dis > dist[node]) continue;
                for(auto& it : adj[node]){
                    int wt = it.second;
                    int anode = it.first;
                    
                    if(dis + wt < dist[anode]){
                        dist[anode] = dis + wt;
                        pq.push({dist[anode], anode});
                    }
                }
            }
            return dist;
        }
    };
```
### Explaination :
 - We use priority queue to find shortest distance
### Reference:
- [GFG-Problem](https://www.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/1)
- [Striver-Video](https://www.youtube.com/watch?v=V6H1qAeB-l4&list=PLgUwDviBIf0oE3gA41TKO2H5bHpPd7fzn&index=32)
