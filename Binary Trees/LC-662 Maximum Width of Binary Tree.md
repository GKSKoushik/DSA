- `TC - O(n)`
- `SC - O(n)`
```cpp
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) {
        queue<pair<TreeNode*, long long >> q;
        if(!root){
            return 0;
        }
        int ans = 0;
        q.push({root, 0});
        while(!q.empty()){
            int size = q.size();
            long long mmin = q.front().second;
            long long first, last;
            for(int i = 0; i < size; i++){
                long long cur_id = q.front().second - mmin;
                TreeNode* node = q.front().first;
                q.pop();
                if(i == 0) first = cur_id;
                if(i == size - 1) last = cur_id;
                if(node->left){
                    q.push({node->left, cur_id*2 + 1});
                }
                if(node->right){
                    q.push({node->right, cur_id*2 + 2});
                }
            }
            ans = max(ans, (int)(last - first + 1));
        }
        return (int)ans;
        
    }
};
```
### Explaination:
- We take root into queue where queue consists of both node and level
- We go till queue is empty each time we check for queue size and store level as min
- Then we go through each and every element in queue, to get out of stack overflow we always make subtractions to get current node as 1
- Then we store node and pop always store that current if as  first and last so that we can check max
- Check node is right or left push it into queue once queue is empty BOOM return the ans.

- [LeetCode-Probelm](https://leetcode.com/problems/maximum-width-of-binary-tree/)
- [Striver-Video](https://www.youtube.com/watch?v=ZbybYvcVLks)

