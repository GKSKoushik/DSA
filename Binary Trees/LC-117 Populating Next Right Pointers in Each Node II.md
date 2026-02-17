- `TC : O(n)`
- `SC : O(w)`
```cpp
class Solution {
public:
    Node* connect(Node* root) {
        if(root == NULL ) return root;
        queue<Node*> q;
        q.push(root);

        while(!q.empty()){
            int size = q.size();
            Node* prev = NULL;
            for(int i = 0; i < size; i++){
                Node* curr = q.front();
                q.pop();

                if(prev != NULL) prev -> next = curr;

                prev = curr;

                if(curr -> left) q.push(curr -> left);
                if(curr -> right) q.push(curr -> right);
            }
            prev -> next = NULL;
        }
        return root;
    }
};
```
### Explaination:
- Here we traverse like level order but we always store last node of that level to set lastnode -> next to NULL
- To do that we keep moving by connecting prev to its nexts not until it reached last node of that level'
### Reference:
- [LeetCode-Problem](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)
- [Algomaster](https://algomaster.io/learn/dsa/populating-next-right-pointers-in-each-node-ii) 
