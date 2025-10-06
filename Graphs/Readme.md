### BFS
`SC : O(n)` <br>
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
Referece BFS:
- [GFG - Problem](https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1)
- [Striver - Video](https://www.youtube.com/watch?v=-tgVpUgsQ5k)

### DFS
`SC : O(n)` <br>
`TC : O(n) + O(2E)`
```cpp
private:
  void dfs(int node, vector<vector<int>> &adj, int vis[], vector<int> &ls){
    vis[node] = 1;
    ls.push_back(node);

    for(auto it : adj[node]){
      if(!vis) {
        dfs(it, adj, vis, ls);
      }
    }
  }
public:
  vector<int> DFS(vector<vector<int>> &adj){
    int V = adj.size();
    int vis[V] = {0};
    int start = 0;
    vector<int> ls;
    dfs(start, adj, vis, ls);

    return ls;
  }
```
Reference:
- [GFG - Problem](https://www.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1)
- [Striver - Video](https://www.youtube.com/watch?v=Qzf1a--rhp8)
