```cpp
//Medium
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        ListNode* temp = head;
        ListNode* track = head;
        int count = 1;
        while(temp->next){
            temp= temp->next;
            count++;
        }
        temp -> next = head;
        k = k % count;
        int newst = count - k;
        for(int i = 1; i<newst;i++) {
            track = track->next;
        }
        temp = track->next;
        track->next = NULL;
        return temp;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/rotate-list/)
- [Striver-Problem](https://www.youtube.com/watch?v=uT7YI7XbTY8)
- There will be slight diffrence with strivers snippet but approach is same
