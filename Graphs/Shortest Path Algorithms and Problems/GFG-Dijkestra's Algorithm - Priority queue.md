TC : O(E logE)
SC : O(V + E)
```cpp
while(!pq.empty()){
    int dis = pq.top().first;
    int node = pq.top().second;
    pq.pop();

    // IMPORTANT LINE
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
```
### Explaination :
 - We use priority queue to find shortest distance
### Reference:
- [GFG-Problem](https://www.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/1)
- [Striver-Video](https://www.youtube.com/watch?v=V6H1qAeB-l4&list=PLgUwDviBIf0oE3gA41TKO2H5bHpPd7fzn&index=32)
