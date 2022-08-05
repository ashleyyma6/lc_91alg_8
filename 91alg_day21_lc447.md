### Idea

- Input：n points in a plain [x,y]
- Goal: find boomerang - (i,j,k) ij=ik
- Output: number of boomerangs
- Distance between two points [x1,y1] [x2,y2] [x3,y3]
  - root of (x2-x1)^2+(y2-y1)^2 compare with root of (x3-x2)^2+(y3-y2)^2
  - Create a hash map for every point {distance:number of points}
  - Traverse number of points, add to result

### Code

```java
public int numberOfBoomerangs(int[][] points) {
        int res = 0;
        for (int[] point1:points){
            HashMap<Double, Integer> map = new HashMap<>();
             for(int[] point2:points){
                 double distance = Math.sqrt((point1[0]-point2[0])*(point1[0]-point2[0])+(point1[1]-point2[1])*(point1[1]-point2[1]));
                 if(map.containsKey(distance)){
                    map.replace(distance, map.get(distance)+1);
                }else{
                    map.put(distance,1);
                }
             }
            Integer[] nums = new Integer[map.size()];
            nums = map.values().toArray(nums);
            for(Integer n:nums){
                if(n.intValue()>1){
                    res += (n.intValue() * (n.intValue()-1));
                }
            }

        }
        return res;
    }
```

**Complexity Analysis**

- Time Complexity: O(n^2)
- Space Complexity: O(n)
