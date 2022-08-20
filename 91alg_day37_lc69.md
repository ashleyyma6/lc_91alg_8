### Idea
- left & right -> subarray , calulate mid, compare mid's power, update left/right for new subarray
### Code

```java
class Solution {
    public int mySqrt(int x) {
        if(x<2){
            return x;
        }
        long left = 2;
        long right = x/2;
        while(left<=right){
            long mid = left+(right-left)/2;
            long midpow = mid*mid;
            if(x>midpow){
                left = mid+1;
            }else if (x<midpow){
                right = mid-1;
            }else{
                return (int)mid;
            }
        }
        return (int)right;
    }
}
```

**Complexity Analysis**

- Time Complexity: O(logn)
- Space Complexity: O(1)
