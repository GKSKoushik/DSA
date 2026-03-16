- TC : O(Height of the tree)
- SC : None as we are not using any extra spaces
```cpp
class Solution {
public:
    TreeNode* last(TreeNode* root){
        if(root -> right == NULL){
            return root;
        }
        return last(root -> right);
    }
    TreeNode* helper(TreeNode* root){
        if(root -> left == NULL){
            return root -> right;
        }
        else if(root -> right == NULL){
            return root -> left;
        }
        TreeNode* rightchild = root -> right;
        TreeNode* lastright = last(root->left);
        lastright -> right = rightchild;
        return root -> left;
    }
    TreeNode* deleteNode(TreeNode* root, int key) {
        if(root == NULL){
            return NULL;
        }
        if(root -> val == key){
            return helper(root);
        }
        TreeNode* dummy = root;
        while(root != NULL){
            if(root -> val > key){
                if(root->left != NULL && root -> left -> val == key){
                    root->left = helper(root->left);
                    break;
                } else {
                    root = root->left;
                }
            } else {
                if(root -> right != NULL && root -> right -> val == key){
                    root -> right = helper(root -> right);
                    break;
                } else {
                    root = root -> right;
                }
            }
        }
        return dummy;
    }
};
```
### Approach:
- We check for value to delete.
- Then we break link by checking if left and right part of tree are available if there are nodes in right and left
- The we take right node and add it to the left nodes last right node (OR)
- We can take left node and add it to the right nodes last left node
### Reference:
- [LeetCode-Problem](https://leetcode.com/problems/delete-node-in-a-bst/)
- [Striver-Video](https://www.youtube.com/watch?v=kouxiP_H5WE)
