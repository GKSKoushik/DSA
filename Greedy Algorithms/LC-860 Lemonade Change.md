- TC : O(n)
- SC : O(1)
```cpp
class Solution {
public:
    bool lemonadeChange(vector<int>& bills) {
        int five = 0, ten = 0;
        for(int i : bills){
            if(i == 5){
                five++;
            }
            else if(i == 10){
                if(five){
                    five--;
                    ten++;
                }
                else{
                    return false;
                }
            }
            else{
                if(five && ten){
                    five--;
                    ten--;
                }
                else if(five >= 3){
                    five -= 3;
                }
                else{
                    return false;
                }
            }
        }
        return true;
    }
};
```
### Explaination:
- We are going keep count of change by any time if when dont have change we return false
- Here changes are 5 , 10, 20 so we keep track of fives and tens as a lemonade costs 5
### Reference:
- [LeetCode-problem](https://leetcode.com/problems/lemonade-change/)
- [Striver-Video](https://www.youtube.com/watch?v=n_tmibEhO6Q)







