```cpp
class Solution {
  public:

    Node *removeDuplicates(struct Node *head) {
        // Your code here
        Node* temp = head;
        while(temp->next && temp){
            Node* dup = temp->next;
            while(dup->data == temp->data && dup){
                Node* del = dup;
                dup = dup->next;
                delete del;
            }
            temp -> next = dup;
            if(dup) dup->prev = temp;
            temp = temp->next;
        }
        return head;
    }
};
```
Reference:
- [Geeks-for-Geeks-Problem](https://www.geeksforgeeks.org/problems/remove-duplicates-from-a-sorted-doubly-linked-list/1)
- [Strivers-Video](https://www.youtube.com/watch?v=YJKVTnOJXSY)
