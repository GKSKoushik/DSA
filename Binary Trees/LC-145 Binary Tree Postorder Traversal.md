Iterative Method
```cpp
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> postorder;
        if( root == NULL) return postorder;        
        stack<TreeNode*> s1 , s2;
        s1.push(root);
        while(!s1.empty()){
            root = s1.top();
            s1.pop();
            s2.push(root);
            if(root->left){
                s1.push(root->left);
            }
            if(root->right){
                s1.push(root->right);
            }
        }
        while(!s2.empty()){
            postorder.push_back(s2.top()->val);
            s2.pop();
        }
        return postorder;
    }
};
```
- [Striver-Video](https://www.youtube.com/watch?v=2YBhNLodD8Q)


Recursive method
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
