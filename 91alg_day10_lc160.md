### Idea
Two pointers traverse list A&B, stop when two pointers point to the same. When a pointer points to none, update pointer to point the head of another list. 
The pointers will meet at the intersectin node or both are None (no intersaction). 
   
### Code

```python
    def getIntersectionNode(self, headA, headB):
        head1 = headA
        head2 = headB
        while head1 != head2:
            head1 = head1.next if head1 else headB
            head2 = head2.next if head2 else headA
        return head1

```

**Complexity Analysis**

- Time Complexity: O(2(n1+n2+n3))
- Space Complexity: O(1)
