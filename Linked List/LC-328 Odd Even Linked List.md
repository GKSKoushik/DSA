```cpp
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if(!head || !head->next) return head;
        ListNode* odd = head;
        ListNode* even = head-> next;
        ListNode* evenhead = head->next;
        while(even !=NULL && even->next != NULL){
            odd->next = odd -> next ->next;
            even->next = even-> next ->next;

            odd = odd->next;
            even = even->next;
        }
        odd->next = evenhead;
        return head;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/odd-even-linked-list/)
- [Strivers-Video](https://www.youtube.com/watch?v=qf6qp7GzD5Q)
