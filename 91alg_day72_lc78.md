### Idea

- Use the bit combinations from 0 to the nums.size to represent the element selected from nums to make that subset. ex, 000, 001, 010. 1 represents element is selected.

### Code

```java

class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        int n = nums.length;
        List<List<Integer>> res = new LinkedList<>();
        for(int i  = 0; i < 1<<n;i++){
            List<Integer> curr = new LinkedList<>();
            for(int j = 0; j<n; j++){
                if((i & (1<<j))==0){
                    curr.add(nums[j]);
                }
            }
            res.add(curr);
        }
        return res;
    }
}

```

**Complexity Analysis**

- Time Complexity:O(n\*2^n)
- Space Complexity:O(1)
