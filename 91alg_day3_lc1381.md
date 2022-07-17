### Idea
- array with 2 pointers
- 1 pointer for stack top, help to judge if exceed max size
- 1 pointer for stack base & increment function, help to judge if empty
- check max & update base when push/pop
- increment: compare k with current top index -> decide the number of element to update

### Code

```python
def __init__(self, maxSize):
        self.stack = [0]*maxSize
        self.max = maxSize-1 # max index
        self.base = -1
        self.top = -1

    def push(self, x):
        if self.top<self.max:
            if(self.top<0):
                self.base+=1
            self.top+=1
            self.stack[self.top]=x
        
    def pop(self):
        if self.top>=0 :
            res = self.stack[self.top]
            self.stack[self.top] = 0
            self.top-=1
            if(self.top<0):
                self.base-=1
            return res
        else:
            return -1
        
    def increment(self, k, val):
        if(self.base>=0):
            if (self.top+1)>=k:
                for i in range(k):
                    self.stack[i]+=val
            else:
                for e in range(self.top+1):
                    self.stack[e]+=val

```

**Complexity Analysis**
- Time Complexity: 
  - push: O(1)
  - pop:O(1)
  - increment: O(n)
- Space Complexity: O(n)