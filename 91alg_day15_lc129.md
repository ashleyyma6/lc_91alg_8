### Idea
- An inner function to traverse the tree, use a variable to store result
- Use a string to collect digits, convert back to int when find all digits
- when the left and right children are none, a number is found

### Code

```python
def sumNumbers(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        s = ""
        res = [0]
        def get_res(root, s):
            s += str(root.val)
            if root.left != None:
                get_res(root.left, s)
            if root.right != None:
                get_res(root.right, s)
            if root.left == None and root.right == None:
                res[0]+=int(s)
            return None
        get_res(root,s)
        return res[0]
```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(1)
