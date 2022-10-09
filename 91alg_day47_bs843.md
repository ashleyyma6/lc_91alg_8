### Idea

### Code

```java

class Solution {
    public int minOperations(int[] nums, int x) {
        int numsSum = 0;
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int i =0; i<nums.length; i++){
            numsSum+=nums[i];
            map.put(numsSum,i);        
        }
        
        map.put(0,0);
        
        int sum = numsSum-x;
        if(sum==0){
            return nums.length;
        }
        int longest = 0;
        int currSum = 0;
        
        for(int left=0;left<nums.length;left++){
            currSum+=nums[left];
            if(map.containsKey(currSum-sum)){
                if(currSum-sum == 0){
                    longest = Math.max(longest, left-map.get(currSum-sum)+1);
                }else{
                    longest = Math.max(longest, left-map.get(currSum-sum));
                }
            }
        }
        int res = 0;
        if(longest==0){
            return -1;
        }else{
            return nums.length-longest;
        }
    }
}

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
