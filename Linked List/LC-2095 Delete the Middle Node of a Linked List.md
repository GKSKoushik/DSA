```cpp
class Solution {
public:
//-------------(Striver-Approach)------------
    ListNode* deleteMiddle(ListNode* head) {
        if(!head || !head->next) return NULL;
        ListNode* slow = head;
        ListNode* fast = head;
        fast = fast->next->next;
        while(fast && fast->next){
            slow = slow->next;
            fast = fast->next->next;
        }
        ListNode* del = slow->next;
        slow->next = slow -> next -> next;
        delete del;
        return head;

//---------------(Optimal)-------------------
        /*if(!head || !head->next) return NULL;

        ListNode* slow = head;
        ListNode* fast = head;
        ListNode* prev = NULL;
        while(fast && fast->next){
            prev = slow;
            slow = slow->next;
            fast = fast->next->next;
        }
        prev->next = slow->next;
        delete slow;
        return head;*/

//------------------(Brute-force)---------------------
        /*if(!head || !head->next) return NULL;
        ListNode* temp = head;
        int cnt = 0;
        while(temp){
            cnt++;
            temp = temp->next;
        }
        cnt=cnt/2;
        temp = head;
        
        for(int i = 0;i<cnt-1;i++){
            temp = temp->next;
        }
        ListNode* del = temp->next;
        temp->next = temp->next->next;
        delete del;
        return head;*/
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)
- [Striver-Video](https://www.youtube.com/watch?v=ePpV-_pfOeI)
