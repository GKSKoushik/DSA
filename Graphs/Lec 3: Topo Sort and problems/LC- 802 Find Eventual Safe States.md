```cpp
class Solution {
public:
    vector<int> eventualSafeNodes(vector<vector<int>>& graph) {
        int n = graph.size();
        vector<vector<int>> revnode(n);
        vector<int> indeg(n,0);
        for(int i = 0 ; i < n; i++ ){
            for(auto it : graph[i]){
                revnode[it].push_back(i);
                indeg[i]++;
            }
        }

        queue<int> q;
        for(int i = 0; i<n ;i++){
            if(indeg[i] == 0){
                q.push(i);
            }
        }

        vector<int> safenode;
        while(!q.empty()){
            int node = q.front();
            q.pop();
            safenode.push_back(node);

            for(auto it : revnode[node]){
                indeg[it]--;
                if(indeg[it] == 0){
                    q.push(it);
                }
            }
        }
        sort(safenode.begin(), safenode.end());
        return safenode;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/find-eventual-safe-states/)
- [Striver-Video](https://www.youtube.com/watch?v=2gtg3VsDGyc)


