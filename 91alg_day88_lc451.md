### Idea

### Code

```cpp
class Solution {
public:
    string frequencySort(string s) {
        unordered_map<char, int> hash;
        priority_queue<pair<int, char>> queue;
        for(auto &ch : s){
            hash[ch]++;
        }
        for(auto &item:hash){
            queue.push({item.second, item.first});
        }
        string res = "";
        while(!queue.empty()){
            auto p = queue.top();
            queue.pop();
            res.append(p.first, p.second);
        }
        return res;
    }
};

```

**Complexity Analysis**

- Time Complexity:O(n)
- Space Complexity:O(n)
