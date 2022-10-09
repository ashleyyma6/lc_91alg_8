### Idea
- sort the array, two pointers at two ends, move inward, try to put max&min together
### Code

```java
class Solution {
    public int numRescueBoats(int[] people, int limit) {
        if(people.length==1){
            return 1;
        }
        Arrays.sort(people);
        int res = 0;
        int low = 0;
        int high = people.length-1;
        while(low<=high){
            if(people[low]+people[high]<=limit){
                res++;
                low++;
                high--;
            }else{
                res++;
                high--;
            }
        }
        return res;
    }
}


```

**Complexity Analysis**

- Time Complexity: O(nlogn)
- Space Complexity: O(nlogn)
