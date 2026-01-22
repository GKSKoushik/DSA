- `TC : O(n)`
- `SC : O(n)`
```cpp
class Solution {
public:
    int maxPathSum(TreeNode* root) {
        int maxi = INT_MIN;
        pathsum(root, maxi);
        return maxi;
    }
    int pathsum(TreeNode* root, int& maxi){
        if(root == 0) return 0;
        int lh = max(0, pathsum(root -> left, maxi));
        int rh = max(0, pathsum(root -> right, maxi));
        maxi = max(maxi, lh + rh + root -> val);
        return max(lh, rh) + root ->val;
    }
};
```
### Explaination
- The whole process fall no recursion where use left hight and right
- It always return max of left node sum or right mode sum + curent node val

- [LeetCode-Problem](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
- [Striver-Video](https://www.youtube.com/watch?v=WszrfSwMz58)
