### Idea

### Code

```java

class MapSum {
    public class Node{
        public int val;
        public HashMap<Character, Node> children;
        public Node(int value){
            val = value;
            children = new HashMap<>();
        }
    }
    public Node root;
    public MapSum() {
        root = new Node(0);
    }

    public void insert(String key, int val) {
        Node curr = root;
        for(char c:key.toCharArray()){
            if(curr.children.get(c) == null){
                curr.children.put(c, new Node(0));
            }
            curr = curr.children.get(c);
        }
        curr.val = val;
    }

    public int sum(String prefix) {
        Node curr = root;
        for(char c:prefix.toCharArray()){
            if(curr.children.get(c)==null){
                return 0;
            }
            curr = curr.children.get(c);
        }
        return treeSum(curr);
    }
    public int treeSum(Node node){
        int res = node.val;
        for(char key: node.children.keySet()){
            res+=treeSum(node.children.get(key));
        }
        return res;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(n)
