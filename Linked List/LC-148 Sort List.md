```cpp
// Used Merge-Sort
class Solution {
public:
    ListNode* midnode(ListNode* node){
        ListNode* slow = node;
        ListNode* fast = node->next;
        while(fast && fast->next){
            slow = slow->next;
            fast = fast->next->next ;
        }
        return slow;
    }
    ListNode* ms(ListNode* leftnode, ListNode* rightnode){
        ListNode* dummy = new ListNode(-1);
        ListNode* temp = dummy;
        while(leftnode && rightnode){
            if(leftnode->val < rightnode->val){
                temp->next = leftnode;
                leftnode = leftnode->next;
            }
            else{
                temp->next = rightnode;
                rightnode = rightnode->next;
            }
            temp = temp -> next;
        }
        if(leftnode) temp->next = leftnode;
        else temp->next = rightnode;


        return dummy->next;
    }

    ListNode* sortList(ListNode* head) {
        if(!head || !head->next) return head;

        ListNode* mid = midnode(head);
        ListNode* lefthead = head;
        ListNode* righthead = mid->next;
        mid->next = NULL;

        lefthead = sortList(lefthead);
        righthead = sortList(righthead);

        return ms(lefthead,righthead);
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/sort-list/)
- [Striver-video](https://www.youtube.com/watch?v=8ocB7a_c-Cc)
