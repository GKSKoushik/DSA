```cpp
class Solution {
public:
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> adj(numCourses);
        for( auto &edge : prerequisites){
            int u = edge[0];
            int v = edge[1];

            adj[u].push_back(v);
        }

        queue<int> q;
        vector<int> indeg(numCourses);
        for(int i = 0; i < numCourses; i++){
            for(auto it : adj[i]){
                indeg[it]++;
            }
        }

        for(int i = 0 ; i < numCourses; i++){
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
                if(indeg[it] == 0) {
                    q.push(it);
                }
            }
        }
        if(topo.size() == numCourses) return true;
        return false;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/course-schedule/description/)
- [Striver-Video](https://www.youtube.com/watch?v=WAOfKpxYHR8)
