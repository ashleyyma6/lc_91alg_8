### Idea
find all connected component (n^2)
find the connected components with one initial infection (m, size of initial)
Choose the largest amount among them (num of connected components)
Choose smallest index if have same largest 
### Code

```python


class UnionFind(object):
    def __init__(self,n):
        self.parents = list(range(n))
        self.sizes = [1]*n
    def find(self, i):
        while i!=self.parents[i]:
            self.parents[i] = self.find(self.parents[i])
            i = self.parents[i]
        return i
       
    def union(self, p, q):
        root_p, root_q = map(self.find, (p,q))
        if(root_p == root_q): return
        small, big = sorted([root_p, root_q], key = lambda x: self.sizes[x])
        self.parents[small]=big
        self.sizes[big]+=self.sizes[small]

            
class Solution:
    
    def minMalwareSpread(self, graph: List[List[int]], initial: List[int]) -> int:
        n = len(graph)
        unionFind = UnionFind(n)
        # find all connected components
        for i in range(n):
            for j in range(n):
                if graph[i][j]: unionFind.union(i,j)
        
        # cound the number of initial infectde nodes of each connected components       
        infected = collections.defaultdict(lambda:0)                
        for i in initial: infected[unionFind.find(i)]+=1
        max_size = 0
        candidate = min(initial)
        for i in initial:
            infection_count = infected[unionFind.find(i)]
            size = unionFind.sizes[unionFind.find(i)]
            if infection_count != 1: continue
            if size > max_size:
                max_size = size
                candidate = i
            elif size == max_size and i< candidate:
                candidate = i
        return candidate
```

**Complexity Analysis**

- Time Complexity: O(n^2)
- Space Complexity: O(n)
