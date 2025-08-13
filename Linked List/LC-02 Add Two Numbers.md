```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* t1 = l1;
        ListNode* t2 = l2;
        ListNode* dummy = new ListNode(-1);
        ListNode* curr = dummy;
        int carry = 0;
        while(t1 || t2) {
            int sum = carry;
            if(t1) sum += t1->val;
            if(t2) sum += t2->val;
            ListNode* newnode = new ListNode(sum%10);
            carry = sum / 10;
            curr->next = newnode;
            curr = curr->next;
            if(t1) t1=t1->next;
            if(t2) t2=t2->next;
        }
        if(carry) {
            ListNode* newnode = new ListNode(carry);
            curr->next = newnode;
            curr = curr->next;
        }
        return dummy->next;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/add-two-numbers/)
- [Striver-Video](https://www.youtube.com/watch?v=XmRrGzR6udg)
