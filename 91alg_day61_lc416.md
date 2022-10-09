### Idea
- the sum of nums must be even, return true when find the sum of some int = the sum of nums / 2
- a decision tree (add current element/not)
  - have a set to save the sum of int in nums
  - backwards traverse nums, add current int with all nums in the set, add back do the set
  - check if target is in set
### Code

```java
class Solution {
    public boolean canPartition(int[] nums) {
        if(nums.length==1){
            return false;
        }
        int sum = IntStream.of(nums).sum();
        System.out.println(sum);
        if(sum%2!=0){
            return false;
        }
        int target = sum/2;
        HashSet<Integer> s = new HashSet<>();
        int n = nums.length;
        s.add(0);
        s.add(nums[n-1]);
        for(int i = n-2;i>=0;i--){
            if(nums[i]==target){
                return true;
            }
            HashSet<Integer> to_add = new HashSet<>();
            to_add = (HashSet<Integer>)s.clone();
            for(Integer e:to_add){
                s.add(e.intValue()+nums[i]);
                if(s.contains(target)){
                    return true;
                }
            }
        }
        return false;
    }
}
```

**Complexity Analysis**

- Time Complexity: O(n * sum(nums))
- Space Complexity: O(sum(nums))
