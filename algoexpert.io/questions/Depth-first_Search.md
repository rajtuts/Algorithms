## Depth First Search

#### Problem Statement


You are given a Node class that has a name and an array of optional children Nodes. When put together, Nodes form a simple tree-like structure. Implement the
depthFirstSearch method on the Node class, which takes in an empty array, traverses the tree using the Depth-rst Search approach (specically navigating the
tree from left to right), stores all the of the Nodes' names in the input array, and returns it.

Sample input:
```
         A
       / | \
      B  C  D
     / \   / \
    E   F G   H
       / \ \
      I  J  K
```
Sample output: ["A","B","E","F","I","J","C","D","G","K","H"]



#### Explanation

We can use a Stack here


#### Solution
```
import java.util.*;

class Program {
    static class Node {
        String name;
        List<Node> children = new ArrayList<Node>();

        public Node(String name) {
            this.name = name;
        }

        // O(v + e) time | O(v) space
        public List<String> depthFirstSearch(List<String> array) {
            array.add(this.name);
            for (int i = 0; i < children.size(); i++) {
                children.get(i).depthFirstSearch(array);
            }
            return array;
        }

        public Node addChild(String name) {
            Node child = new Node(name);
            children.add(child);
            return this;
        }
    }
}

```

Check this [Python](../python/Depth_First_Search.py) code.

