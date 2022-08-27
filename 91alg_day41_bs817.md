### Idea

- Binary Search Space [0, max-min]
- left = 0, right = max-min
- count the number of pair abs smaller than mid, if count<k, k is not in [0,mid], check [mid,right]
- 2 pointers to count distance<k

### Code

```java
class Solution {
    public int solve(int[] nums, int k) {
        Arrays.sort(nums);
        int n = nums.length;
        int left = 0;
        int right = nums[n-1]-nums[0];
        while(left<=right){
            int mid = (right+left)/2;
            if(count(nums,mid)<=k){
                left=mid+1;
            }else{
                right=mid-1;
            }
        }
        return left;
    }
    public int count(int[] nums, int mid){
        int count = 0;
        int left = 0;
        for(int right = 1; right<nums.length;right++){
            while(nums[right]-nums[left]>mid){
                left++;
            }
            count+=(right-left);
        }
        return count;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(nlogn)
- Space Complexity: O(1)
