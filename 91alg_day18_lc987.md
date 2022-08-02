### Idea
- DFS, put all nodes in corresponding column list in tuple format (row, value)
- use center_index to track root's 0th column list, do calculation to get other nodes' corresponding list
- Get [[(row, value),(row, value)],[(row, value),(row, value)]]
- For every sublist: Sort by row in (row, value) -> sort value if two row are the same

### Code

```python
    def __init__(self):
        self.center_index = 0
        
    def verticalTraversal(self, root):
        res = []
        tuple_list = []
        def find_pos(root, row, col):
            if root == None:
                return None
            if len(tuple_list) == 0:
                new_list = [(row,root.val)]
                tuple_list.append(new_list)
                self.center_index = col
            else:
                need_list_index = self.center_index + col
                if need_list_index<0:
                    new_list = [(row,root.val)]
                    tuple_list.insert(0,new_list)
                    self.center_index+=1
                elif need_list_index>=len(tuple_list):
                    new_list = [(row,root.val)]
                    tuple_list.append(new_list)
                else:
                    tuple_list[need_list_index].append((row,root.val))
            find_pos(root.left, row+1, col-1)
            find_pos(root.right, row+1, col+1)
        find_pos(root,0,0)
        for l in tuple_list:
            res.append(self.sort_list(l))
        return res
    def sort_list(self, list):
        list.sort()
        pre_row = list[0][0]
        res = []
        temp = []
        i = 0
        print(list)
        while i<len(list):
            if pre_row == list[i][0]:
                temp.append(list[i][1])
                i+=1
            else:
                temp.sort()
                res+=temp
                temp = []
                pre_row = list[i][0]
        temp.sort()
        res+=temp
        return res
```

**Complexity Analysis**

- Time Complexity: O(n)+O(n log n)+O(n log n) = O(n log n) (?)
- Space Complexity: O(n)+O(n) = O(n)
