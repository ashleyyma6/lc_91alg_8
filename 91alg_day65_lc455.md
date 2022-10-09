### Idea
- sort g and s
- if s[i] <= g[i], all cookies after s[i] can satisfy g[i], all greedy after g[i] cannot be satisfied by s[i]
- check if s[i] <= g[i]
  - yes: move to next g[i]
  - move to next s[i]
### Code

```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int g_pointer = 0;
        int s_pointer = 0;
        while (s_pointer < s.length && g_pointer<g.length){
            if(s[s_pointer] >= g[g_pointer]){
                g_pointer++;
            }
            s_pointer++;
        }
        return g_pointer;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(nlogn)
- Space Complexity: O(nlogn)
