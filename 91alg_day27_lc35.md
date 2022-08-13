### Idea
- Left and right pointer point to the start and the end of the array, calculate the element in the middle, compare with the target, if mid smaller than the target, move to check the right sub array, if bigger than the target, move to check the left sub array, until left is larger than right. 
- When mid equal to the target, return mid, if cannot find a mid, return left. 

### Code

```java
public int searchInsert(int[] nums, int target) {
        int left  = 0;
        int mid = 0;
        int right = nums.length-1;
        while(left<=right){
            mid = (right-left)/2+left;
            if(target == nums[mid]){
                return mid;
            }
            if(target>nums[mid]){
                left = mid+1;
            }else{
                right = mid-1;
            }
        }
        return left;
    }

```

**Complexity Analysis**

- Time Complexity: O(logn)
- Space Complexity: O(1)
