### Idea
- Fast and slow pointer will meet if there is a loop. 
- If pointer points to None, there is no cycle. 
- After fast pointer and slow pointer meet, update fast pointer point to head. 
- Move fast and slow pointer one node at a time until they meet at the cycle entry. 

### Code

```python
def detectCycle(self, head):
        fast = head
        slow = head
        while fast != None and fast.next!=None:
            fast = fast.next.next
            slow = slow.next
            if fast == slow:
                break
        if fast==None or fast.next==None:
            return None
        fast = head
        while fast!=slow:
            fast=fast.next
            slow=slow.next
        return fast
```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(1)
