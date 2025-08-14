```cpp
Node * deleteAllOccurrences(Node* head, int k) {
    // Write your code here
    Node* temp = head;
    while(temp){
        if(temp->data == k){
            if(head->data == k){
                head = head->next;
            }
            Node* nextnode = temp -> next;
            Node* prevnode = temp -> prev;

            if(nextnode) nextnode->prev = prevnode;
            if(prevnode) prevnode->next = nextnode;
            delete temp;
            temp = nextnode;
        }
        else temp = temp->next;
    }
    return head;
}
```
Reference:
- [Code-360-Problem](https://www.naukri.com/code360/problems/delete-all-occurrences-of-a-given-key-in-a-doubly-linked-list_8160461?leftPanelTabValue=SUBMISSION)
- [Striver-Video](https://www.youtube.com/watch?v=Mh0NH_SD92k)
