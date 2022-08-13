### Idea

- one pointer mark the index of the last put number
- one pointer to traverse array nums
- when current checking number is different from last put number = meet a new number -> put the new number

### Code

```java
public int removeDuplicates(int[] nums) {
    int put = 0;
    for(int i = 0;i<nums.length;i++){
        if(nums[put]!=nums[i]){
            put++;
            nums[put]=nums[i];
        }
    }
    return put+1;
}
```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(1)
