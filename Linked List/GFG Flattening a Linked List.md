```cpp
class Solution {
  public:
    // Function which returns the  root of the flattened linked list.
//-----------------Recursion-------------------
    Node* mergelist(Node* list1, Node* list2){
        Node* dummy = new Node(-1);
        Node* res = dummy;
        while(list1 && list2){
            if(list1->data < list2->data){
                res -> bottom = list1;
                res = list1;
                list1 = list1->bottom;
            }
            else{
                res -> bottom = list2;
                res =  list2;
                list2 = list2->bottom;
            }
            res->next = NULL;
        }
        if(list1) res->bottom = list1;
        else res->bottom = list2;
        
        return dummy->bottom;
    }
    Node *flatten(Node *root) {
        // Your code here
        
        if(!root || !root->next ) return root;
        
        Node* newhead = flatten(root->next);
        
        mergelist(root, newhead);
        
        return root;
        
        
//-------------Brute-Force--------------        
       /* Node* temp = root;
        vector<int> nums;
        while(temp){
            Node* t2 = temp;
            while(t2){
                nums.push_back(t2->data);
                t2 = t2 -> bottom;
            }
            temp = temp->next;
        }
        if(nums.size() == NULL) return NULL; 
        sort(nums.begin(),nums.end());
        Node* newlist = new Node(nums[0]);
        Node* curr = newlist;
        for(int i = 1; i < nums.size();i++){
            Node* newnode = new Node(nums[i]);
            curr->bottom = newnode;
            curr = curr->bottom;
        }
        return newlist;*/
    }
};
```
Reference:
- [Geeks-for-Geeks-Problem](https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1)
- [Strivers-Video](https://www.youtube.com/watch?v=ykelywHJWLg)






