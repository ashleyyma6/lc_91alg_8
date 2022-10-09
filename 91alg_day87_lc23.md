### Idea
- merge two by two

### Code

```cpp
class Solution {
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        int n = lists.size();
        if(n==0){
            return nullptr;
        }
        if(n==1){
            return lists.front();
        }
        while(lists.size()>1){
            vector<ListNode*> newLists;
            for(int i = 0;i+1<lists.size();i+=2){
                ListNode *merged = megerTwo(lists[i], lists[i+1]);
                newLists.push_back(merged);
            }
            if(lists.size() & 0x01){
                newLists.push_back(lists.back());
            }
            lists = vector<ListNode*>(newLists.begin(), newLists.end());
        }
        return lists[0];
    }
private:
    ListNode *megerTwo(ListNode *L1, ListNode *L2){
        ListNode *pre = new ListNode(-1);
        ListNode *head = pre;
        while(L1!=nullptr && L2!= nullptr){
            if(L1->val < L2->val){
                head->next = L1;
                L1 = L1->next;
            }else{
                head->next = L2;
                L2 = L2->next;
            }
            head=head->next;
        }
        if(L1!=nullptr){
            head->next = L1;
        }
        if(L2!= nullptr){
            head->next = L2;
        }
        return pre->next;
    }
};

```

**Complexity Analysis**

- Time Complexity:O(kn)
- Space Complexity:O(1)
