```cpp
class Solution {
public:
    int lenght(ListNode* slow, ListNode* fast){
        int count = 1;
        fast = fast->next;
        while(slow != fast){
            count++;
            fast = fast->next;
        }
        return count;
    }
    int findLengthOfLoop(ListNode *head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast && fast->next){
            slow = slow->next;
            fast = fast->next->next;
            if(slow == fast){
                return lenght(slow,fast);
            }

        }
        return 0;
    }
};
```
Reference:
- [Tuf-Problem](https://takeuforward.org/plus/dsa/problems/length-of-loop-in-ll?tab=editorial)
- [Striver-Video](https://www.youtube.com/watch?v=I4g1qbkTPus)
