### Idea
- Tree -> array str -> Tree
- root -> Left subtree -> Right subtree, recursive

### Code

```python
def serialize(self, root):
        res = []
        def se(root):
            if root == None:
                res.append('null')
                return res
            curr = str(root.val)
            res.append(curr)
            se(root.left)
            se(root.right)
        se(root)
        print(res)
        return str(res)
            
    def deserialize(self, data):
        data = data[1:-1].replace("'","").split(', ')
        print(data)
        def de(data):
            if len(data)==1 and data[0]=='null':
                return None
            val = data[0]
            data.remove(val)
            if val=='null':
                return None
            root = TreeNode(int(val))
            root.left = de(data)
            root.right = de(data)
            return root
        
        return de(data)

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
