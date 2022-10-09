### Idea
- A map to save the relative horizontal distance of the node from root node (left child -1, right child +1), and the level of node in a tuple, 
- updating the node's tuple that is in minimum level
  
### Code

```python
class Solution:
    
    def traversal(self, root,dist,level,dic):
        if root is None:
            return
        if dist not in dic or level<dic[dist][1]:
            dic[dist] = (root.val, level)
        self.traversal(root.left,dist-1,level+1,dic)
        self.traversal(root.right,dist+1,level+1,dic)

    def solve(self, root):
        dic = {}
        self.traversal(root,0,0,dic)
        result = []
        for val in sorted(dic.keys()):
            result.append(dic.get(val)[0])
        return result

```

**Complexity Analysis**

- Time Complexity: O(log(n))
- Space Complexity: O(n)
