### Idea
1. check if the left subarray is smaller than the right subarray, if smaller, get a new chunck
2. Traversal, get the max of left subarray and the min of right subarray, compare

### Code

```python
def maxChunksToSorted(self, arr):

    length = len(arr)
    left = [0]*length
    right = [0]*length
    
    for i in range(len(arr)):
        if i == 0:
            left[i]=arr[i]
        else:
            left[i]=max(left[i-1],arr[i])
    
    for i in reversed(range(len(arr))):
        if i == length-1:
            right[i]=arr[i]
        else:
            right[i]=min(right[i+1],arr[i])
    res = 0
    for i in range(len(arr)-1):
        if left[i]<=right[i+1]:
            res+=1
    return res+1
```

**Complexity Analysis**

- Time Complexity:O(n)+O(n)+O(n)=O(n)
- Space Complexity:O(n)+O(n)=O(n)
