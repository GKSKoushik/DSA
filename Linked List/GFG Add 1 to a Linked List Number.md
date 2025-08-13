```cpp
class Solution {
  public:
  
    int helper(Node* head) {
        if(!head) {
            return 1;
        }
        int carry = helper(head->next);
        head->data = head->data + carry;
        if(head->data < 10) return 0;
        head->data = 0;
        return 1;
    }
    
    Node* addOne(Node* head) {
        int carry = helper(head);
        if(carry == 1){
            Node* temp = new Node(1);
            temp->next = head;
            head = temp;
        }
        return head;
    }
};
```
Reference:
- [Geeks-for-Geeks-Problem](https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1)
- [Strivers-Video](https://www.youtube.com/watch?v=aXQWhbvT3w0)
