### Idea
1. a dictionary to track the key and its node
2. a linked list to manage LRU cache
### Code

```python
class ListNode(object):
    def __init__(self, key, val):
        self.key = key
        self.val = val
        self.next = None
        self.pre = None
    
class LRUCache(object):

    def __init__(self, capacity):
        self.capacity = capacity
        self.size = 0
        self.addr = {}
        self.head = ListNode(-1,-1)
        self.tail = ListNode(-1,-1)
        self.head.next = self.tail
        self.tail.pre = self.head

    def get(self, key):
        if key in self.addr:
            node = self.addr[key]
            self.remove(node)
            self.add(node)
            return node.val
        else:
            return -1

    def put(self, key, value):
        if key in self.addr:
            node = self.addr[key]
            node.val = value
            self.remove(node)
            self.add(node)
        else:
            node = ListNode(key,value)
            self.addr[key] = node
            self.add(node)
            if(self.size<self.capacity):
                self.size+=1
            else:
                tailKey = self.removeTail()
                del self.addr[tailKey]

    def remove(self, node):
        pre = node.pre
        nex = node.next
        pre.next = nex
        nex.pre = pre
    
    def add(self, node):
        node.pre = self.head
        node.next = self.head.next
        self.head.next.pre = node
        self.head.next = node
        
    def removeTail(self):
        node = self.tail.pre
        self.remove(node)
        return node.key


```

**Complexity Analysis**

- Time Complexity:O(1) for get, put
- Space Complexity:O(n)
