### Idea

- need a pre head/pre pointer before the first node for node swap
- need a pointer to mark the first node in the pair
- need a temp pointer (always .next of the first node) for the second node in the pair to do node swap

### Code

```python
        if(head == None or head.next == None):
            return head

        pre = ListNode(0)
        pre.next = head

        p0 = pre
        p1 = head
        while(p1!=None and p1.next!=None):
            p2 = p1.next
            p0.next = p2
            p1.next = p2.next
            p2.next = p1
            p0=p0.next.next
            p1=p1.next
        return pre.next

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(1)
