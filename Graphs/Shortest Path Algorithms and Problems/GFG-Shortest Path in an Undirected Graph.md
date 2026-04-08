- TC : O(E logV) + O(N) dijkstrs's + Destiantion to source check
- SC : O(E) + O(V) + O(V) + O(E) + O(V) = O(V + E) Adj + Dist + Parent + Priority Queue + Path
```cpp
class Solution {
  public:
    vector<int> shortestPath(int n, int m, vector<vector<int>>& edges) {
        // Code here
        vector<vector<pair<int,int>>> adj(n+1);
        for(auto& it : edges){
            adj[it[0]].push_back({it[1], it[2]});
            adj[it[1]].push_back({it[0], it[2]});
        }
        priority_queue<pair<int,int>, vector<pair<int,int>>, greater<pair<int, int>>> pq;
        pq.push({0, 1});
        vector<int> parent(n+1), dist(n+1, 1e9);
        for(int i = 1; i < parent.size(); i++) parent[i] = i;
        dist[1] = 0;
        while(!pq.empty()){
            auto it = pq.top();
            int node = it.second;
            int wt  = it.first;
            pq.pop();
            if(wt > dist[node]) continue;
            for(auto& it : adj[node]){
                int adjnode = it.first;
                int edw = it.second;
                if(wt + edw < dist[adjnode]){
                    dist[adjnode] = wt + edw;
                    pq.push({dist[adjnode], adjnode});
                    parent[adjnode] = node;
                }
            }
        }
        if(dist[n] == 1e9) return {-1};
        vector<int> path;
        int node = n;
        while(parent[node] != node){
            path.push_back(node);
            node = parent[node];
        }
        path.push_back(1);
        reverse(path.begin(), path.end());
        path.insert(path.begin(), dist[n]);
        return path;
        
    }
};
```
### Explaination:
 - Here we use adj list pairs to store adj values and its weights, parent list to store the node form which its coming, dist list to store all minimum weighs, and a priority queue pairs to store weights and nodes
 - As usual we do like BFS stuff but we here we are not only pushing values to the queue we also change parent list
 - We will not go to all the paths we check condition if current path weight is greater than the previous weight which is "dist[node]" the we just contiue
 - After all we check if there is no a way from source to destination the we return "{-1}"
 - Then we start from destination node to source we figure the path and we insert the weight for the path in front of path list and return path
### Reference:
 - [GFG-Problem](https://www.geeksforgeeks.org/problems/shortest-path-in-weighted-undirected-graph/1)
 - [Striver-Video](https://www.youtube.com/watch?v=rp1SMw7HSO8&list=PLgUwDviBIf0oE3gA41TKO2H5bHpPd7fzn&index=35)


