### Idea
- start from the last int in nums, move forward check the longest increasing subsequence after it, traverse all elements in the back, and record the maximum subsequence length and the number of it. 
- a previous int's maximum subsequence length is the maximum subsequence length of the number larger than it after it + 1, the number of subsequences is that maximum subsequence number. 
- updating the longest subsequence length and updating the number of the subsequence when looping forward.
### Code

```java
class Solution {
    public int findNumberOfLIS(int[] nums) {
        HashMap<Integer, int[]> dp = new HashMap<>();
        int longest = 0;
        int res = 0;
        for(int i = nums.length-1;i>=0;i--){
            int max_len = 1;
            int max_cnt = 1;
            for(int j = i+1;j<nums.length;j++){
                if(nums[j]>nums[i]){
                    int len = dp.get(j)[0];
                    int cnt = dp.get(j)[1];
                    if(len+1 > max_len){
                        max_len = len+1;
                        max_cnt = cnt;
                    }else if(len+1 == max_len){
                        max_cnt += cnt;
                    }
                }
            }
            if(max_len > longest){
                longest = max_len;
                res = max_cnt;
            }else if (max_len == longest){
                res += max_cnt;
            }
            dp.put(i, new int[]{max_len, max_cnt});
        }
        return res;
    }
}

```

**Complexity Analysis**

- Time Complexity:O(n^2)
- Space Complexity:O(n)
