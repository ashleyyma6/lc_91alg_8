### Idea
- 1st loop: find all indices of *c*
- 2nd loop: get abs min for all elements in *s*
### Code
```python
def shortestToChar(self, s, c):
        index = []
        res = [0]*len(s)
        for i in range(len(s)):
            if s[i] == c:
                index.append(i)
        for i in range(len(s)):
            if i in index:
                res[i]=0
            else:
                res[i] = min([abs(i-x) for x in index])
        return res
```

**Complexity Analysis**
- Time Complexity: O(n^2)
- Space Complexity: O(n)