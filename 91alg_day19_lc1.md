### Idea
- Traverse nums
- If target - current number is not in the dictionary, add {current number : index} to the dictionary
- If target - current number is in the dictionary, return the index of target - current number and current number
### Code

```python
def twoSum(self, nums, target):
    dic = {}
    for i in range(len(nums)):
        if target-nums[i] in dic:
            return [dic[target-nums[i]],i]
        else:
            dic[nums[i]]=i
    return None

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
