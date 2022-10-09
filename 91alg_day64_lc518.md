### Idea

### Code

```java
class Solution {
    public int change(int amount, int[] coins) {
        int[][] dp = new int[amount+1][coins.length+1];
        Arrays.fill(dp[0],1);
        for(int i = 1; i<=amount; i++){
            for(int j = coins.length-1; j>=0;j--){
                dp[i][j] = dp[i][j+1];
                if(i-coins[j] >= 0){
                    dp[i][j] += dp[i-coins[j]][j];
                }
            }
        }
        return dp[amount][0];
    }
}
```

**Complexity Analysis**

- Time Complexity:O(m*n) // m = amount, n = # of coins
- Space Complexity:O(m*n)
