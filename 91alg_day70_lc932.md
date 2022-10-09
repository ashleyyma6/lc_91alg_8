### Idea

### Code

```java
class Solution {
    public int[] beautifulArray(int n) {
        HashMap<Integer, int[]> map = new HashMap<>();
        return dividenconquer(map, n);
    }
    public int[] dividenconquer(HashMap<Integer, int[]> map, int n){
        if(map.containsKey(n)){
            return map.get(n);
        }
        int[] res = new int[n];
        if(n==1){
            res[0]=1;
        }else{
            int j = 0;
            for(int i:dividenconquer(map,(n+1)/2)){
                res[j]=2*i-1;
                j++;
            }
            for(int i:dividenconquer(map, n/2)){
                res[j]=2*i;
                j++;
            }
        }
        map.put(n, res);
        return res;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(nlogn)
- Space Complexity: O(nlogn)
