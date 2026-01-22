- `TC - O(n)`
- `SC - O(n)` 
```cpp
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>> result;
        if(root == NULL){
            return result;
        }
        bool isleftright = true;
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty()){
            int qsize = q.size();
            vector<int> row(qsize);
            for(int i = 0; i < qsize; i++){
                TreeNode* node = q.front();
                q.pop();

                int index = (isleftright) ? i : qsize - i- 1;

                row[index] = node -> val;
                if(node -> left){
                    q.push(node -> left);
                }
                if(node -> right){
                    q.push(node -> right);
                }
            }
            isleftright = !isleftright;
            result.push_back(row);

        }
        return result;
    }
};
```
### Question
- Traversing zig zag in a tree.
### Explaination
 - We start from root and push it into q then we use bool for toggle zig and zag
 - We got till queue is not empty and we always calculate size of q and we also take vetor of that q size
 - We got through the size of q and we take fromt node and pop it
 - We take index value as if its zig or zag we keep going left and right till level ends
 - Once for loop is ended we toggle the bool the we push the zig or zag vector to 2D vector then we return the 2D vector.

- [LeetCode-Problem](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
- [Striver-Video](https://www.youtube.com/watch?v=3OXWEdlIGl4)




