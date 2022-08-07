### Idea
- fast pointer move two nodes at a time, slow pointer move one node at a time
- when faster pointer reaches the end, slow pointer is in the middle.

### Code

```python
    public ListNode middleNode(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while(fast!= null && fast.next != null){
            fast = fast.next.next;
            slow=slow.next;
        }
        return slow;
    }
```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(1)
