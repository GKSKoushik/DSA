TC : O(n+n)+log256  Log is due to map SC : O(256)
```cpp
int kDistinctChars(int k, string &str)
{
    // Write your code here
    int l = 0, r= 0 ,  maxlen = 0;
    map<char , int> mpp;

    while(r < str.size()){
        mpp[str[r]]++;
        while(mpp.size() > k){
            mpp[str[l]]--;
            if(mpp[str[l]] == 0) mpp.erase(str[l]);
            l++;
        }
        maxlen = max(maxlen,r-l+1);
        r++;
    }

    return maxlen;
}
```    
TC : O(n)+log256  SC : O(256)
```cpp
int kDistinctChars(int k, string &str)
{
    int l = 0, r= 0 ,  maxlen = 0;
    map<char , int> mpp;

    while(r < str.size()){
        mpp[str[r]]++;
        if(mpp.size() > k){
            mpp[str[l]]--;
            if(mpp[str[l]] == 0) mpp.erase(str[l]);
            l++;
        }
        if(mpp.size() <= k) maxlen = max(maxlen,r-l+1);
        r++;
    }

    return maxlen;
}
```



