```cpp
class Solution {
public:

//Optimal - approach
    ListNode* reverse(ListNode* head){
        if(head == nullptr || head->next == nullptr){
            return head;
        }
        ListNode* newnode = reverse(head->next);
        ListNode* front = head -> next;
        front -> next = head;
        head->next = NULL;
        return newnode;
    }
    bool isPalindrome(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast->next && fast->next->next){
            slow = slow->next;
            fast = fast->next->next;
        }
        ListNode* newnode = reverse(slow->next);
        ListNode* first = head;
        ListNode* second = newnode;
        while(second){
            if(first->val != second -> val){
                reverse(newnode);
                return false;
            }
            first = first -> next;
            second = second -> next;
        }
        reverse(newnode);
        return true;



//---------------------------------
//Brute-force
        /*stack<int> st;
        ListNode* temp = head;
        while(temp!=nullptr){
            st.push(temp->val);
            temp = temp->next;
        }
        temp = head;
        while(temp!=nullptr){
            if(temp->val != st.top()){
                return false;
            }
             st.pop();
            temp = temp -> next;
        }
        return true;*/
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/palindrome-linked-list/)
- [Strivers-Video](https://www.youtube.com/watch?v=lRY_G-u_8jk)
