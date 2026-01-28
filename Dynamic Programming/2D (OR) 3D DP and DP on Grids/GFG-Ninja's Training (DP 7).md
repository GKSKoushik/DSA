- `TC : O(n)`
- `SC : O(n)` 
```cpp
class Solution {
  public:
  
    int f(int day, int last, vector<vector<int>> &points, vector<vector<int>> &dp){
        if(day == 0){
            int maxi = 0;
            for(int task = 0; task < 3; task++){
                if(task != last){
                    maxi = max(maxi, points[0][task]);
                }
            }
            return maxi;
        }
        
        if(dp[day][last] != -1) return dp[day][last];
        int maxi = 0;
        for(int task = 0; task < 3; task++){
            if(task != last){
                int point = points[day][task] + f(day - 1, task, points,dp);
                maxi = max(maxi, point);
            }
        }
        return dp[day][last]=maxi;
    }   
     
    int maximumPoints(vector<vector<int>>& mat) {
        // code here
        int n = mat.size();
        vector<vector<int>> dp(n, vector<int>(4 ,-1));
        return f(n-1, 3 , mat, dp);
    }
};
```
### Question
- An 2D array size of N * 3 consists of day and 3 diffrent activites 
- Lets assume {0, 1 , 2} are activites and it runs for 4 days 
- If activity {0} is performed in day 1 then same activity should lot be performed in day 2
- While performing these activites we should find maximum of all days

### Explaination:
- The Base case is if we are in day 0 then we have then ther wont be any day called {-1}th day so day 0 Becomes last
- We keep recurse till it reaches day 0 once it reaches day 0 we come back with the returns
- Each time we return we check with the dp array and return

### Reference:
- [Geeks-for-Geeks-Problem](https://www.geeksforgeeks.org/problems/geeks-training/1)
- [Striver-Video](https://www.youtube.com/watch?v=AE39gJYuRog)


