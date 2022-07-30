### Idea

- find the length of list, k%length find the rotatin needed
- need to switch two sublists, list splits at length-k
- one pointer for the end of right sublist
- one pointer for the end of left sublist

### Code

```python
def rotateRight(self, head, k):
    if k==0:
        return head
    if head==None or head.next==None:
        return head

    length = 0
    p1 = head
    while p1 != None:
        length+=1
        p1 = p1.next

    rotate = k%length

    p1 = head
    while rotate>0:
        p1 = p1.next
        rotate-=1
    p2 = head
    while p1.next!=None:
        p1=p1.next
        p2=p2.next
    p1.next = head
    head = p2.next
    p2.next = None
    return head

```

**Complexity Analysis**

- Time Complexity: O(n)+O(n)=O(n)
- Space Complexity: O(1)
