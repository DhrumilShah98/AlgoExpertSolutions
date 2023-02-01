# Branch Sums

## Problem

Write a function that takes in a Binary Tree and returns a list of its branch sums ordered from leftmost branch sum to rightmost branch sum.

A branch sum is the sum of all values in a Binary Tree branch. A Binary Tree branch is a path of nodes in a tree that starts at the root node and ends at any leaf node.

Each `BinaryTree` node has an integer `value`, a `left` child node, and a `right` child node. Children nodes can either be `BinaryTree` nodes themselves or `None`/`null`.

Sample Input

```
tree =     1
        /     \
       2       3
     /   \    /  \
    4     5  6    7
  /   \  /
 8    9 10
```

Sample Output

```
[15, 16, 18, 10, 11]
```

#

## Approach 1: Recursive

```JAVA
import java.util.List;
import java.util.ArrayList;

class Program {
  // This is the class of the input root. Do not edit it.
  public static class BinaryTree {
    int value;
    BinaryTree left;
    BinaryTree right;

    BinaryTree(int value) {
      this.value = value;
      this.left = null;
      this.right = null;
    }
  }

  /**
  * Approach 1: Recursive
  *
  * Time Complexity: O(N), where N is number of nodes in binary tree.
  * Space Complexity: O(N), where N is number of nodes in binary tree.
  *
  * @param root  root node in binary tree.
  */
  public static List<Integer> branchSums(BinaryTree root) {
    List<Integer> result = new ArrayList<Integer>();
    calculateBranchSums(root, 0, result);
    return result;
  }

  public static void calculateBranchSums(BinaryTree node, int runningSum, List<Integer> result) {
    if (node == null) return;

    runningSum += node.value;
    if(node.left == null && node.right == null){
      result.add(runningSum);
      return;
    }

    calculateBranchSums(node.left, runningSum, result);
    calculateBranchSums(node.right, runningSum, result);
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is number of nodes in binary tree.
- Space Complexity: O(N), where N is number of nodes in binary tree.
