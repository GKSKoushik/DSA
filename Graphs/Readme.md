### BFS
SC : O(n) <br>
`TC : O(n) + O(2E)     *E for edges`
```cpp
vector bfs(vector<vector<int>> &adj){
  int vis[adj.size()] = {0};
  vis[0] = 1;
  queue<int> queue;
  q.push(0);
  vector<int> bfs;
  while(!q.empty()){
    int node = q.front();
    q.pop();
    bfs.push_back(node);

    for(auto it : adj[node]){
      if(!vis[it]){
        vis[it] = 1;
        q.push(it);
      }  
    }
    return dfs;
  }
}
```
