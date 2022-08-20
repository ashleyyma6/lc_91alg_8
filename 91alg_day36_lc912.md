### Idea
- Iterative Quick Sort
### Code

```java
class Solution {
    public int[] sortArray(int[] nums) {
        quickSort(nums,0,nums.length-1);
        return nums;
    }
    public void quickSort(int[] nums, int left, int right){
        if(left<right){
            int i = left;
            int j = right;
            int pivot = nums[left];
            while(i<j){
                while(i<j && nums[j] > pivot){
                    j--;
                }
                nums[i]=nums[j];
                i++;
                while(i<j && nums[i] < pivot){
                    i++;
                }
                nums[j]=nums[i];
                j--;
            }
            nums[i] = pivot;
            quickSort(nums, left, i-1);
            quickSort(nums, j+1, right);
            
        }
    }
}

```

**Complexity Analysis**

- Time Complexity: O(nlogn)
- Space Complexity: O(n)
