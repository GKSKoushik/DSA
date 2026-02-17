### Recursion
- `TC - O(n)`
- `SC - O(H) H - Height of tree`
```cpp
class Solution {
public:
    void f(vector<int>& ans, TreeNode* node, int level ){
        if(node == NULL) return;

        if(level == ans.size()){
            ans.push_back(node -> val);
        }
        f(ans, node -> right, level + 1);
        f(ans, node -> left, level + 1);
        
    }
    vector<int> rightSideView(TreeNode* root) {
        vector<int> ans;
        f(ans, root, 0);
        return ans;
    }
};
```
### Explaination:  Recurssion Call(vector(ans), pass(root), we pass the level which is 0)
- Whenever we reach null we just return
- We always check if level == size of array so that we push the {node -> value} to the ans(vector)
- While we keep incrementing the level, array size and level never gets equal more than once on same level, this helps to skip other value on same level
- we goto right then left it because we want right side view if we want left side we we do alternate, We always increment level whenever we got right or left
### Reference:
- [LeetCode-Problem](https://leetcode.com/problems/binary-tree-right-side-view/)
- [Striver-Video](https://www.youtube.com/watch?v=KV4mRzTjlAk&t=53s)
