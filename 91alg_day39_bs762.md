### Idea
- get the range of R [0, (nums[-1]-nums[0])/3], binary serach a valid R within it
- validation: try to put lights, if need more than 3 lights, R is invalid. 

### Code

```java
class Solution {
    public double solve(int[] nums) {
        Arrays.sort(nums);
        int left = 0;
        int right = (nums[nums.length-1]-nums[0])/3;
        while(left<=right){
            int mid = left+(right-left)/2;
            if(validate(nums, mid)){
                right = mid-1;
            }else{
                left = mid+1;
            }
        }
        if(validate(nums,left)){
            return (double)left/2;
        }
        return (double)right/2;
        
    }
    public boolean validate(int[] nums, int r){
        int covered = -1;
        int lights = 0;
        for(int i = 0; i< nums.length;i++){
            if(nums[i]>covered){
                lights++;
                covered = nums[i]+r;
            }
            if(lights>3){
                return false;
            }
        }
        return true;
    }
}


```

**Complexity Analysis**

- Time Complexity: O(nlogn + nlogm)) // m = R serach space
- Space Complexity: O(nlogn)
