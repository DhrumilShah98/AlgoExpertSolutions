# Node Depths

## Problem

The distance between a node in a Binary Tree and the tree's root is called the node's depth.

Write a function that takes in a Binary Tree and returns the sum of its nodes' depths.

Each `BinaryTree` node has an integer `value`, a `left` child node, and a `right` child node. Children nodes can either be `BinaryTree` nodes themselves or `None`/`null`.

Sample Input

```
tree =     1
        /     \
       2       3
     /   \    /  \
    4     5  6    7
  /   \
 8    9
```

Sample Output

```
16
```

#

## Appraoch 1: Recursive

### First Way

```JAVA
class Program {

  /**
  * Approach 1: Recursive
  *
  * 1. Average Case
  *     - Time Complexity: O(N), where N is the number of nodes in the tree.
  *     - Space Complexity: O(H), where H is the tree's height.
  * 2. Worst Case
  *     - Time Complexity: O(N), where N is the number of nodes in the tree.
  *     - Space Complexity: O(N), where N is the number of nodes in the tree.
  *
  * @param node  current node in the tree.
  * @param sum  sum of the nodes' depth.
  * @param level  current node's level/depth.
  */
  private static int nodeDepths(BinaryTree node, int sum, int level) {
    if(node == null) return sum;
    sum += level;
    sum = nodeDepths(node.left, sum, level + 1);
    sum = nodeDepths(node.right, sum, level + 1);
    return sum;
  }

  public static int nodeDepths(BinaryTree root) {
    return nodeDepths(root, 0, 0);
  }

  static class BinaryTree {
    int value;
    BinaryTree left;
    BinaryTree right;

    public BinaryTree(int value) {
      this.value = value;
      left = null;
      right = null;
    }
  }
}

```

### Second Way

```JAVA
class Program {
  /**
  * Approach 1: Recursive
  *
  * 1. Average Case
  *     - Time Complexity: O(N), where N is the number of nodes in the tree.
  *     - Space Complexity: O(H), where H is the tree's height.
  * 2. Worst Case
  *     - Time Complexity: O(N), where N is the number of nodes in the tree.
  *     - Space Complexity: O(N), where N is the number of nodes in the tree.
  *
  * @param node  current node in the tree.
  * @param level  current node's level/depth.
  */
  private static int nodeDepths(BinaryTree node, int level) {
    if(node == null) return 0;
    return level + nodeDepths(node.left, level + 1) + nodeDepths(node.right, level + 1);
  }

  public static int nodeDepths(BinaryTree root) {
    return nodeDepths(root, 0);
  }

  static class BinaryTree {
    int value;
    BinaryTree left;
    BinaryTree right;

    public BinaryTree(int value) {
      this.value = value;
      left = null;
      right = null;
    }
  }
}

```

### Complexity Analysis

1. Average Case
   - Time Complexity: O(N), where N is the number of nodes in the tree.
   - Space Complexity: O(H), where H is the tree's height.
2. Worst Case
   - Time Complexity: O(N), where N is the number of nodes in the tree.
   - Space Complexity: O(N), where N is the number of nodes in the tree.
