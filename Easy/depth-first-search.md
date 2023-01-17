# Depth First Search

## Problem

You're given a `Node` class that has a `name` and an array of optional `children` nodes. When put together, nodes form an acyclic tree-like structure.

Implement the `depthFirstSearch` method on the `Node` class, which takes in an empty array, traverses the tree using the Depth-first Search approach (specifically navigating the tree from left to right), stores all of the nodes' names in the input array, and returns it.

Sample Input

```
graph = A
     /  |  \
    B   C   D
   / \     / \
  E   F   G   H
     / \   \
    I   J   K
```

Sample Output

```
["A", "B", "E", "F", "I", "J", "C", "D", "G", "K", "H"]
```

#

## Approach 1: Depth First Search Algorithm

```JAVA
import java.util.*;

class Program {
  // Do not edit the class below except
  // for the depthFirstSearch method.
  // Feel free to add new properties
  // and methods to the class.
  static class Node {
    String name;
    List<Node> children = new ArrayList<Node>();

    public Node(String name) {
      this.name = name;
    }

    /**
    * Approach 1: Depth First Search Algorithm
    * V: Denotes the number of vertices in the input graph.
    * E: Denotes the number of edges in the input graph.
    *
    * Time Complexity: O(V + E).
    * Space Complexity: O(V).
    *
    * @param array  input array of size N.
    * @param targetSum  target sum to achieve.
    */
    public List<String> depthFirstSearch(List<String> array) {
      array.add(this.name);
      for(Node child: children){
        child.depthFirstSearch(array);
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

### Complexity Analysis

- Time Complexity: O(V + E).
  - V: Denotes the number of vertices in the input graph.
  - E: Denotes the number of edges in the input graph.
- Space Complexity: O(V).
  - V: Denotes the number of vertices in the input graph.
