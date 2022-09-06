### Idea
- Check the middle, if the middle is true, check left subarray, else, check right subarray, update left/right
### Code

```java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int left = 0;
        int right = n-1;
        while(left<=right){
            int mid = left+(right-left)/2;
            if(isBadVersion(mid)){
                if(!isBadVersion(mid-1)){
                    return mid;
                }else{
                    right=mid-1;
                }
            }else{
                left = mid+1;
            }
        }
        return n;
    }
}
```

**Complexity Analysis**

- Time Complexity: O(logn)
- Space Complexity: O(1)
