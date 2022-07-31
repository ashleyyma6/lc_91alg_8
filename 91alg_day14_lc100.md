### Idea
Traverse two trees together, compare their current nodes. 
### Code

```python
    def isSameTree(self, p, q):
        if p == None and q == None:
            return True
        if p == None and q!= None:
            return False
        if p!= None and q == None:
            return False
        if (p.val==q.val):
            return True and self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
        else:
            return False

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
