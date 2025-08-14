```cpp
//Recursive solution
class Solution {
public:
    double myPow(double x, int n) {
        if(n == 0 ) return 1;
        if(n < 0 ) return 1/myPow(x,-n);
        
        double half = myPow(x,n/2);
        if(n % 2 == 0){
            return half * half;
        }
        else{
            return half * half * x;
        }
    }
};
```
Reference:
- [LeetCode-Problem](https://leetcode.com/problems/powx-n/)
- [Striver-Video](https://www.youtube.com/watch?v=l0YC3876qxg)
