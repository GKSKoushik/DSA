```cpp
class Solution {
public:
    Node* copyRandomList(Node* head) {
        Node* temp = head;
        while(temp){
            Node* copy = new Node(temp->val);
            copy->next = temp->next;
            temp->next = copy;
            temp = temp -> next ->next;
        }
        temp = head;
        Node* dummy = new Node(-1);

        while(temp){
            Node* copyn = temp->next;
            copyn = temp ->next;
            if(temp->random) copyn->random = temp -> random -> next;
            else copyn->random = nullptr;
            temp = temp -> next -> next;
        }
        Node* dummyn = new Node(-1);
        Node* res = dummyn;
        temp = head;
        while(temp){
            res->next = temp->next;
            temp->next = temp->next->next;
            temp = temp->next;
            res = res->next;
        }
        return dummyn->next;
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/copy-list-with-random-pointer/)
- [Striver-Video](https://www.youtube.com/watch?v=q570bKdrnlw)


