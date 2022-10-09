### Idea
- Divide and conquer. Merge two lists, and merge the merged lists, continue untill merged into one list.
  
### Code

```python
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        if(lists.length == 0){
            return null;
        }
        return merge(lists, 0, lists.length-1);
    }
    public ListNode merge(ListNode[] lists, int start, int end){
        if(start==end){
            return lists[start];
        }
        int mid = start+(end-start)/2;
        ListNode left = merge(lists, start, mid);
        ListNode right = merge(lists, mid+1, end);
        
        ListNode pre = new ListNode(0);
        ListNode head = pre;
        while(left != null && right != null){
            if(left.val<right.val){
                head.next = left;
                head = left;
                left = left.next;
            }else{
                head.next = right;
                head = right;
                right = right.next;
            }
        }
        if(left!= null){
            head.next = left;
        }else{
            head.next = right;
        }
        return pre.next;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(nlog(m)) // n = # of linked list nodes, m = # of lists
- Space Complexity: O(1)
