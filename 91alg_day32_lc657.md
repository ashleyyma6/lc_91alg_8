### Idea
- Keep two local variables x,y for the position changes in 2D
- Upate x, y based on the move
- Check if x, y is 0 at the end
### Code

```java
public boolean judgeCircle(String moves) {
        int x = 0;
        int y = 0;
        for(char move: moves.toCharArray()){
            switch(move){
                case 'R':
                    x+=1;
                    break;
                case 'L':
                    x-=1;
                    break;
                case 'U':
                    y+=1;
                    break;
                case 'D':
                    y-=1;
                    break;
                default:
                    break;
            }
        }
        return (x==0 && y==0);
    }

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
