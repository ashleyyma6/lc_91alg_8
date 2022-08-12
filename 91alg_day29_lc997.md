### Idea

- Mark people who trust someone else
- Count how many people trust the person who do not trust anyone else
- If the trust count is equal to n-1, that person is judge

### Code

```java
public int findJudge(int n, int[][] trust) {
    if(n==1){
        return 1;
    }
    int[] trusted = new int[n];
    for(int[] arr: trust){
        trusted[arr[0]-1]=-1;
        if(trusted[arr[1]-1]!=-1){
            trusted[arr[1]-1]+=1;
        }
    }
    for(int i =0;i<n;i++){
        if(trusted[i]==(n-1)){
            return i+1;
        }
    }
    return -1;
}
```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
