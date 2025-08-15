```cpp
//Hard-Level
class Solution {
public:
    ListNode* reverse(ListNode* temp){
        ListNode* prev = NULL;
        ListNode* cuur = temp;
        while(cuur){
            ListNode* nextnode = cuur->next;
            cuur->next = prev;
            prev = cuur;
            cuur = nextnode;
        }
        return prev;
    }
    ListNode* findkth(ListNode* temp,int k) {
        k -= 1;
        while(temp && k > 0){
            temp = temp -> next;
            k--;
        }
        return temp;
    }
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* temp = head;
        ListNode* prev = NULL;
        while(temp){
            ListNode* kthn = findkth(temp, k);
            if(!kthn){
                if(prev) {
                    prev->next = temp;
                }
                break;
            }
            ListNode* nexn = kthn->next;
            kthn->next = NULL;
            ListNode* newhead = reverse(temp);
            if(temp == head){
                head = newhead;
            }
            else {
                prev->next = newhead;
                    
            }
            prev = temp;
            temp = nexn; 
        }
        return head;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/reverse-nodes-in-k-group/)
- [Striver-Video](https://www.youtube.com/watch?v=lIar1skcQYI)




