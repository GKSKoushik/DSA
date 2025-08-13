```cpp
class Solution {
  public:
    Node* segregate(Node* head) {
        Node* zeros = new Node(-1);
        Node* ones = new Node(-1);
        Node* twos = new Node(-1);
        Node* temp = head;
        
        Node* zeroshead = zeros;
        Node* oneshead = ones;
        Node* twoshead = twos;
        if(!head || !head->next) return head;
        
        while(temp){
            if(temp->data == 0){
                zeros->next = temp;
                zeros = zeros->next;
            }
            else if(temp->data == 1){
                ones->next = temp;
                ones = ones->next;
            }
            else{
                twos->next = temp;
                twos = twos->next;
            }
            temp = temp -> next;
        }
        zeros->next = (oneshead->next)?oneshead->next:twoshead->next;
        ones->next = twoshead->next;
        twos->next = NULL;
        
        Node* newnode = zeroshead->next;
        
        delete zeroshead;
        delete twoshead;
        delete oneshead;
        
        return newnode;
      
    }
};
```
Reference :
- [Geeks-for-Geeks-Problem](https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1)
- [Strivers-Video](https://www.youtube.com/watch?v=gRII7LhdJWc)
