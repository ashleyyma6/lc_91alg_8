### Idea

Input: an int in array form **num**, an int **k** to add
Output: result in array form

1. array to int, add k, int to array
   ~~2. int k to array, add array~~

### Code

```python
    def addToArrayForm(self, num, k):
        # array to int
        int_res = int(''.join(str(n) for n in num))
        int_res+=k
        # int to array
        res = [int(n) for n in str(int_res)]
        return res
```

**Complexity Analysis**

- Time Complexity: O(n)+O(n) = O(n)
- Space Complexity: O(1)+O(n) = O(n)

### Trash

```
    # k to arr

    str_k = str(k)
    arr_k = []
    for c in str_k:
        arr_k.append(int(c))
    #print arr_k

    raise = 0
    index_k = len(arr_k)-1
    index_num = len(num)-1
    while(index_k>=0 and index_num>=0):
        temp = arr_k[index_k]+num[index_num]
        if(raise==1):
            temp+=1
            raise = 0
        if(temp>9):
            temp%=10
            raise = 1
        index
```
