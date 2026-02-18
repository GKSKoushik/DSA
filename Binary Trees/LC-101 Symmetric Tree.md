```cpp
class Solution {
public:
    bool same(TreeNode* p, TreeNode* q){
        if(p == NULL || q == NULL) return (p==q);
        return (p->val == q->val) &&
            same(p->left, q->right) && 
            same(p->right, q->left);
    }
    bool isSymmetric(TreeNode* root) {
        TreeNode* lroot = root -> left;
        TreeNode* rroot = root -> right;
        return same(lroot, rroot);
    }
};
```
### Hint:
- Its Same as Same Tree Problem 
- Here we need to check for mirror tree buy skiping root
### Reference:
- [LeetCode-Problem](https://leetcode.com/problems/symmetric-tree/submissions/1923545892/)
- [Striver-Video](https://www.youtube.com/watch?v=nKggNAiEpBE)
