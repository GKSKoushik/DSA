TC : O(n) SC : O(n)
```cpp
class Solution {
public:
    int dfsheight(TreeNode* root,int& maxi){
        if(!root) return 0;

        int lf = dfsheight(root->left,maxi);
        int rf = dfsheight(root->right,maxi);
        maxi = max(maxi,lf+rf);

        return 1+max(lf,rf);
    }
    int diameterOfBinaryTree(TreeNode* root) {
        int maxi=0;
        dfsheight(root,maxi);
        return maxi;
    }
};
```

TC: O(n^2)
```cpp
class Solution {
public:
    int fheight(TreeNode* root){
        if(!root) return 0;

        return 1+max(fheight(root->left),fheight(root->right));
    }
    int diameterOfBinaryTree(TreeNode* root) {
        if(!root) return 0;

        int lf = fheight(root->left);
        int rf = fheight(root->right);

        int curr = lf+rf;
        int lef = diameterOfBinaryTree(root->left);
        int rig = diameterOfBinaryTree(root->right);

        return max(curr,max(lef,rig));
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/diameter-of-binary-tree/)
- [Striver-Video](https://www.youtube.com/watch?v=Rezetez59Nk)
