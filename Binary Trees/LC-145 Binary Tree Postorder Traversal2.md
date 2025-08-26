Iterative method
```cpp
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> result;
        if(!root) return{};
        vector<int> left = postorderTraversal(root->left);
        result.insert(result.end(),left.begin(),left.end());

        vector<int> right = postorderTraversal(root->right);
        result.insert(result.end(),right.begin(),right.end());

        result.push_back(root->val);

        return result;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/binary-tree-postorder-traversal/)
- [Striver-Video](https://www.youtube.com/watch?v=COQOU6klsBg)
