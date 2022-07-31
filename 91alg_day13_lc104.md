### Idea
Find the max between left child tree maxDepth and right child tree maxDepth, +1 to get the current node's maxDepth. 

### Code

```python
    def maxDepth(self, root):
        if root == None:
            return 0
        res = 1 + max(self.maxDepth(root.left),self.maxDepth(root.right))
        return res

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
