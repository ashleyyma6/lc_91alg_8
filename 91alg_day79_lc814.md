### Idea

### Code

```python
class Solution:
    def pruneTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root==None:
            return False
        return root if self.containsOne(root) else None
    def containsOne(self, node):
        if node==None:
            return False
        left = self.containsOne(node.left)
        right = self.containsOne(node.right)
        if left == False:
            node.left = None
        if right == False:
            node.right = None
        return (node.val==1) or left or right

```

**Complexity Analysis**

- Time Complexity: O(n) // n = number of nodes
- Space Complexity: O(m) // m = hight of tree
