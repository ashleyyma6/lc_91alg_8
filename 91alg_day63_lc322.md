### Idea
- make an dp array of size amount
- base case dp[0] = 0, 0 coins for 0
- for every coin, fill the dp array with the min number of coin need to reach a specific account

### Code

```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        if(amount == 0){
            return 0;
        }
        int[] dp = new int[amount+1];
        Arrays.fill(dp,Integer.MAX_VALUE);
        dp[0] = 0;
        for(int coin : coins){
            for(int i = 0; i<amount+1;i++){
                if(i-coin>=0 && dp[i-coin] != Integer.MAX_VALUE){
                    dp[i] = Math.min(dp[i], dp[i-coin]+1);
                }
            }
        }
        if (dp[amount] != Integer. MAX_VALUE){
            return dp[amount];
        }else{
            return -1;
        }
    }
}

```

**Complexity Analysis**

- Time Complexity: O(n*len(coins))
- Space Complexity: O(n)
