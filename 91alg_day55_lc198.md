### Idea

- Have int[] dp to save the maximum can steal when reach i-th house
- when reach i-th house, the next house to steal is i+2 and i+3
  - conversely, when reach to i-th house, its maximum is found from the maximum between "dp[i-1]" (house i is not visited) and "nums[i] + the maximun between dp[i-2] and dp[i-3] "(house i is visited)
  - the last one in dp[] is the maximun can steal

### Code

```python
class Solution {
    public int rob(int[] nums) {
        if(nums.length==1){
            return nums[0];
        }
        if(nums.length==2){
            return Math.max(nums[0],nums[1]);
        }
        int n = nums.length;
        int dp[] = new int[n];
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0],nums[1]);
        dp[2] = Math.max(nums[2]+dp[0],nums[1]);
        for(int i = 3;i<n;i++){
            dp[i] = Math.max(nums[i]+Math.max(dp[i-2],dp[i-3]),dp[i-1]);
        }
        return dp[n-1];
    }
}
```

**Complexity Analysis**

- Time Complexity:O(n)
- Space Complexity: O(n)
