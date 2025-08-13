```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* fast = head;
        ListNode* slow = head;
        for(int i = 0 ;i<n;i++){
            fast = fast->next;
        }
        if(!fast) return head->next;
        while(fast->next){
            slow = slow->next;
            fast = fast->next;
        }
        ListNode* del = slow -> next;
        slow->next = slow->next->next;
        delete del;
        return head;
    }
};
```
References:
-[LeetCode - problem](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)
-[Strivers - Video](https://www.youtube.com/watch?v=3kMKYQ2wNIU)
