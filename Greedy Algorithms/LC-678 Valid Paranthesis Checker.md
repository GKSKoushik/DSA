- TC : O(n)
- SC : O(1)
```cpp
class Solution {
public:
    bool checkValidString(string s) {
        int min = 0, max = 0;
        for(char ch : s){
            if(ch == '('){
                min++;
                max++;
            }
            else if(ch == ')'){
                min--;
                max--;
            }
            else{
                min--;
                max++;
            }
            if(min < 0) min = 0;
            if(max < 0) return false;
        }
        return (min == 0);
    }
};
```
### Explaination:
- We always keep track of min and max by anytime if we go max < 0 then we are false as string may look like ")("
- At the end min should always == 0 as we keep adding * max may increase but when min < 0  we are making min = 0
