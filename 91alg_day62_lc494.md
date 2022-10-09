### Idea
- possible sum [-sum(num),sum(nums)] -> make the dp array [nums.length][sum(nums)*2+1]
- fill the dp array (decision tree) dp[i][j] = dp[i-1][j-nums[i]] +  dp[i-1][j+nums[i]]
- base case:
  - first element is 0, 2 ways: +0, -0 
  - not 0, mid is at index"sum", the root is at (0,0) -> (0,sum), then the first level is filled at [0][sum-nums[0]] and [0][sum+nums[0]] 
### Code

```java
class Solution {
    public int findTargetSumWays(int[] nums, int target) {
        int sum = Arrays.stream(nums).sum();
        if(Math.abs(sum)<Math.abs(target)){
            return 0;
        }
        int n = nums.length;
        int t = sum*2+1;
        int[][] dp = new int[n][t];
        if(nums[0]==0){
            dp[0][sum] = 2;
        }else{
            dp[0][sum+nums[0]]=1;
            dp[0][sum-nums[0]]=1;
        }
        for(int i = 1; i<n;i++){
            for(int j = 0;j<t;j++){
                int left = 0;
                if(j-nums[i]>=0){
                    left = j-nums[i];
                }
                int right = 0;
                if(j+nums[i]<t){
                    right = j+nums[i];
                }
                dp[i][j] = dp[i-1][left]+dp[i-1][right];
            }
        }
        return dp[n-1][target+sum];
    }
}
```

**Complexity Analysis**

- Time Complexity: O(n*sum(nums))
- Space Complexity: O(n*sum(nums))
