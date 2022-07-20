### Idea
1. Traverse *s*
   1. push number to stack *num*
   2. push [ & characters to stack *char*, until meet ]
   3. when meet ], pop stack *char* & add characters together until meet [
   4. pop the stack *num*,  decode characters, push result back to stack *char*
2. return stack *char* content
### Code

```python
def decodeString(self, s):
        num = []
        char = []
        i = 0
        while i < len(s):
            if s[i].isdigit():
                n = ""
                while(s[i].isdigit()):
                    n+=s[i]
                    i+=1
                num.append(int(n))
            elif s[i] == ']':
                tmp = ""
                while char[-1]!='[':
                    tmp = char.pop()+tmp
                char.pop()
                tmp = tmp*num.pop()
                char.append(tmp)
                i+=1
            else:
                char.append(s[i])
                i+=1
        res = ""
        while len(char)>0:
            res = char.pop()+res
        return res
```

**Complexity Analysis**

- Time Complexity:O(n)+O(n)+O(n)=O(n)
- Space Complexity:O(n)
