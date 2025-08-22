The template for Sliding window Where it helps most of time\
Algo:
```cpp
  arr = [2,5,1,10,10] , k =14 , arrsize = arr.size();
  Left = 0; Right = 0, Maxlen =0;
    while(Right<n)
    {
      sum = sum + arrsize[Right];
      while(sum>k)
      {
          sum = sum - arr[Right]
          Left = Left + 1
      }
      if(sum <= k )
      {
          maxlen = max(maxlen, Right-Left-1);
      }
      Right = Right + 1;
    }
  return maxlen;           
```
This Gives time Complexity of O(n + n)\
To reduse it to O(n) we make inner while loop to if condition\
Algo:
```cpp
  arr = [2,5,1,10,10] , k =14 , arrsize = arr.size();
  Left = 0; Right = 0, Maxlen =0;
    while(Right<n)
    {
      sum = sum + arrsize[Right];
      if(sum>k)
      {
          sum = sum - arr[Right]
          Left = Left + 1
      }
      if(sum <= k )
      {
          maxlen = max(maxlen, Right-Left-1);
      }
      Right = Right + 1;
    }
  return maxlen;           
```
This algorithm is used when there is no need to reduce the window size\
In few cases algo might differ
