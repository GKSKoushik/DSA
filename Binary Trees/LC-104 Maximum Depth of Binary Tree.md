TC : O(n)  SC : (n)
```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root==nullptr) return 0;

        int lef=maxDepth(root->left);
        int rig=maxDepth(root->right);

        return 1+max(lef,rig);
    }
};
```
Reference:
- [LeetCode-problem](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)
- [Striver-Video](https://www.youtube.com/watch?v=eD3tmO66aBA)
