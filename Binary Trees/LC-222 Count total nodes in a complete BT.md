- `TC - O(n)`
- `SC - O(h)`
```cpp
class Solution {
public:
    void level(TreeNode* node, int& count){
        if(node == NULL ) return;
        count++;
        level(node -> left, count);
        level(node -> right, count);
    }
    int countNodes(TreeNode* root) {
        int count  = 0;
        level(root, count);
        return count;  
    }
};
```
### Explaination
 - Go to the every node call inorder/preorder/postorder and count nodes
- TC -  O(log<sup>2</sup> n)
- SC - O(h)
```cpp
class Solution {
public:
    int right(TreeNode* root){
        int h = 0;
        while(root != NULL){
            h++;
            root = root -> right;
        }
        return h;
    }
    int left(TreeNode* root){
        int h = 0;
        while(root != NULL){
            h++;
            root = root->left;
        }
        return h;
    }
    int countNodes(TreeNode* root) {
        if(!root) return 0;

        int lh = left(root);
        int rh = right(root);

        if(lh == rh) return (1 << lh) - 1;

        return 1 + countNodes(root -> left) + countNodes(root -> right);
    }
};
```
### Explaination
 - We use formula to find nodes $2^n$ - 1
 - If the given tree is not full binary tree we always check for sub full tree and we always add thoese unfull treenodes
### Reference:
 - [LeetCode-Problem](https://leetcode.com/problems/count-complete-tree-nodes/)
 - [Striver-Video](https://www.youtube.com/watch?v=u-yWemKGWO0)
