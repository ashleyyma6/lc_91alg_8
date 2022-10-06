### Idea

### Code

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        int p1 = 0; // for hay
        int p2 = 0; // for nee
        int start = -1;
        while(p1<haystack.size() && p2<needle.size()){
            if(haystack[p1] == needle[p2]){
                if(start<0){
                    start = p1;
                }
                p1++;
                p2++;
            }else{
                if(start > -1){
                    p1 = start;
                    start=-1;
                }
                p1++;
                p2=0;
            }
        }

        if(p2 == needle.size() && start>-1){
            return start;
        }else{
            return -1;
        }
    }
};

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(1)
