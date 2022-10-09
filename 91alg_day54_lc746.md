### Idea
- int array dp will save the past costs to step from level i
- make 1 step to level i will get dp[i-1]+cost[i], make two step will get dp[i-2]+cost[i], the smaller one is the cost
- return the minimun cost of step from the last 1 level and step from the last 2 level
### Code

```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        if(cost.length ==2){
            return Math.min(cost[0], cost[1]);
        }
        int[] dp = new int[cost.length];
        dp[0] = cost[0];
        dp[1] = cost[1];
        for(int i = 2;i<cost.length;i++){
            dp[i] = cost[i]+ Math.min(dp[i-1],dp[i-2]);
        }
        return Math.min(dp[cost.length-1],dp[cost.length-2]);
    }
}
```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(1)
