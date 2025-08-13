```cpp
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast && fast->next){
            slow = slow->next;
            fast = fast->next->next;
            if(slow==fast){
                ListNode* ptr1 = head;
                ListNode* ptr2 = slow;
                while(ptr1 != ptr2){
                    ptr1=ptr1->next;
                    ptr2=ptr2->next;
                }
                return ptr1;
            }
        }
        return nullptr;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/linked-list-cycle-ii/description/)
- [Strivrs-Video](https://www.youtube.com/watch?v=2Kd0KKmmHFc)
