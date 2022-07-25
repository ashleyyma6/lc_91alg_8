### Idea
1. linked list -> array -> tree
2. root of the tree/subtree is at middle of the array/subarray
3. left/right subtree is build from left/right subarray


### Code

```python
    def sortedListToBST(self, head):
        arr = []
        while head:
            arr.append(head.val)
            head = head.next
        return self.buildTree(arr)
    
    def buildTree(self, arr):
        if len(arr)==0:
            return None
        mid = len(arr)//2
        root = TreeNode(arr[mid])
        root.left = self.buildTree(arr[:mid])
        root.right = self.buildTree(arr[mid+1:])
        return root
```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
