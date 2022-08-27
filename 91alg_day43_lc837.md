### Idea
- DP[i] = DP[i-1]xP(1)+DP[i-2]xP(2)+...+DP[i-maxPts]xP(maxPts) = (1/maxPts)(DP[i-1]+DP[i-2]+...+DP[i-maxPts])
- DP[i-1] = (1/maxPts)(DP[i-2]+DP[i-3]+...+DP[i-1-maxPts])
- The differences between DP[i] and DP[i-1] are "DP[i-1]" and "DP[i-1-maxPts]"
- Use sliding widnow to add "DP[i-1]" and remove "DP[i-1-maxPts]"
- Corner case: 
  - i-maxPts in DP[i-maxPts] must > 0
  - There is no DP[i-1] if i-1>=k
  - If n>=k+maxPts, no matter how to draw, result will <= n

### Code

```java
class Solution {
    public double new21Game(int n, int k, int maxPts) {
        if(k == 0 || n >= k+maxPts){
            return 1.0;
        }
        double[] dp = new double[n+1];
        dp[0] = 1.0;
        double sum = dp[0];
        double result = 0.0;
        for(int i = 1;i<=n;i++){
            dp[i] = sum/(double)maxPts;
            if(i<k){
                sum+=dp[i];
            }else{
                result+=dp[i];
            }
            if(i-maxPts>=0){
                sum-=dp[i-maxPts];
            }
        }
        return result;
    }
}
```

**Complexity Analysis**

- Time Complexity: O(N)
- Space Complexity: O(N)
