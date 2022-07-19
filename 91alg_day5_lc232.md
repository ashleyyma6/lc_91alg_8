### Idea

- push: push to stack1
- pop: pop from stack2
  - if stack2 is empty, move stack1 content to stack2 first
- peek: return the first element of stack2
  - if stack2 is empty, move stack1 content to stack2 first
- empty: return if stack1 and stack2 all empty
- check empty before pop, peek

### Code

```python
class MyQueue(object):

    def __init__(self):
        self.stack1=[]
        self.stack2=[]

    def push(self, x):
        self.stack1.append(x)

    def pop(self):
        if not self.empty():
            if len(self.stack2)==0:
                while len(self.stack1)>0:
                    self.stack2.append(self.stack1[-1])
                    self.stack1.pop(-1)
            return self.stack2.pop()
        else: return None

    def peek(self):
        if not self.empty():
            if len(self.stack2)==0:
                while len(self.stack1)>0:
                    self.stack2.append(self.stack1[-1])
                    self.stack1.pop(-1)
            return self.stack2[-1]
        else: return None

    def empty(self):
        return len(self.stack1)+len(self.stack2) == 0
```

**Complexity Analysis**

- Time Complexity:
  - push: O(1)
  - pop: O(n)
  - peek: O(n)
  - empty: O(1)
- Space Complexity: O(n)
