```cpp
class Solution {
  public:
//-----------------Optimal-------------------
    Node* findtail(Node* head){
        Node* tail = head;
        while(tail->next){
            tail = tail->next;
        }
        return tail;
        
    }
    vector<pair<int, int>> findPairsWithGivenSum(Node *head, int target) {
        vector<pair<int,int>> sums;
        Node* start = head;
        Node* tail = findtail(head);
        while(start->data < tail->data){
            if(start->data + tail->data == target){
                sums.push_back({start->data,tail->data});
                start = start->next;
                tail = tail->prev;
            }
            else if(start->data + tail->data < target){
                start = start->next;
            }
            else{
                tail = tail->prev;
            }
        }
        return sums;
        
        
//--------------Brute-Force-------------------
//It will not run all cases due to TIME EXCEED Error
        /*vector<pair<int,int>> sums;
        Node* temp1 = head;
        while(temp1->next){
            Node* temp2 = temp1->next;
            while(temp2){
                if(temp1->data + temp2->data == target){
                    sums.push_back(make_pair(temp1->data,temp2->data));
                }
                temp2 = temp2->next;
            }
            temp1 = temp1->next;
        }
        return sums;*/
    }
```
Reference:
- [Geeks-for-Geeks-Problem](https://www.geeksforgeeks.org/problems/find-pairs-with-given-sum-in-doubly-linked-list/1)
- [Strivers-Video](https://www.youtube.com/watch?v=YitR4dQsddE)



};
