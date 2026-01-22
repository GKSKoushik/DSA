```cpp
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p == NULL || q == NULL){
            return (p == q);
        }
        return (p -> val == q -> val) &&
                isSameTree(p -> left, q -> left) &&
                isSameTree(p -> right, q -> right);
    }
};
```
### Explaination
- Check and comapre each node from both trees

- [LeetCode-Problem](https://leetcode.com/problems/same-tree/)
- [Striver-Video](https://www.youtube.com/watch?v=BhuvF_-PWS0)
