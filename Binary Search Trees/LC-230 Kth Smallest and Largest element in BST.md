- TC : O(n)
- SC : O(n)
```cpp
class Solution {
public:
    int go(TreeNode* root, int k, int& cnt){
        if(root == NULL) return -1;
        int left = go(root-> left, k, cnt);
        if(left != -1) return left;
        cnt++;
        if(cnt == k)  return root->val;
        return go(root->right, k , cnt);
    }
    int kthSmallest(TreeNode* root, int k) {
        int cnt = 0;
        return go(root, k, cnt);
    }
};
```
### Approach:
- Inorder Traversal it always comes in ascending order as the tree is BST
- When count == k the we return that value
### Reference:
- [LeetCode-Problem](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)
- [Striver-Video](https://www.youtube.com/watch?v=9TJYWh0adfk)
