TC : O(n) SC : O(n)
```cpp
class Solution {
public:
    int dfsheight(TreeNode* root){
        if(!root) return 0;

        int lh = dfsheight(root->left);
        if(lh == -1) return -1;
        int rh = dfsheight(root->right);
        if(rh == -1) return -1;

        if(abs(lh-rh)>1) return -1;

        return 1+max(lh,rh);
    }

    bool isBalanced(TreeNode* root) {
        return dfsheight(root) != -1;
    }
};
```
TC : O(n^2) 
```cpp
class Solution {
public:
    int maxdepth(TreeNode* root){
        if(!root) return 0;

        return 1+max(maxdepth(root->right),maxdepth(root->left));
    }
    bool isBalanced(TreeNode* root) {
        if(!root) return true;

        int lh = maxdepth(root->left);
        int rh = maxdepth(root->right);

        if(abs(lh-rh) > 1) return false;

        bool lef = isBalanced(root->left);
        bool rig = isBalanced(root->right);

        if(!lef || !rig) return false;

        return true;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/balanced-binary-tree/)
- [Striver-Video](https://www.youtube.com/watch?v=Yt50Jfbd8Po)
