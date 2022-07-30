### Idea

BFS, get the lowest level nodes, return the first one

### Code

```python
 def findBottomLeftValue(self, root):
        res = None
        arr = []
        arr.append(root)
        while len(arr):
            curr = arr
            arr = []
            for i in range(len(curr)):
                if(curr[i].left):
                    arr.append(curr[i].left)
                if(curr[i].right):
                    arr.append(curr[i].right)
            res = curr
        return (res[0].val)
```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
