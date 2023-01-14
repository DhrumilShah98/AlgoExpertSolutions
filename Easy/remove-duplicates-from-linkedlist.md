# Remove Duplicates From Linked List

## Problem

You're given the head of a Singly Linked List whose nodes are in sorted order with respect to their values. Write a function that returns a modified version of the Linked List that doesn't contain any nodes with duplicate values. The Linked List should be modified in place (i.e., you shouldn't create a brand new list), and the modified Linked List should still have its nodes sorted with respect to their values.

Each `LinkedList` node has an integer `value` as well as a `next` node pointing to the next node in the list or to `None`/`null` if it's the tail of the list.

Sample Input

```
linkedlist = 1 -> 1 -> 3 -> 4 -> 4 -> 4 -> 5 -> 6 -> 6
// the head node with value 1
```

Sample Output

```
1 -> 3 -> 4 -> 5 -> 6 // the head node with value 1
```

#

## Approach 1: LinkedList Single Pass

```JAVA
class Program {
  // This is an input class. Do not edit.
  public static class LinkedList {
    public int value;
    public LinkedList next;

    public LinkedList(int value) {
      this.value = value;
      this.next = null;
    }
  }

  /**
  * Approach 1: LinkedList Single Pass
  *
  * Time Complexity: O(N), where N is the length of the linked list.
  * Space Complexity: O(1).
  *
  * @param linkedList  head of the singly linked list.
  */
  public LinkedList removeDuplicatesFromLinkedList(LinkedList linkedList) {
    LinkedList currentNode = linkedList;
    while(currentNode.next != null){
      if(currentNode.next.value == currentNode.value){
        currentNode.next = currentNode.next.next;
      } else {
        currentNode = currentNode.next;
      }
    }
    return linkedList;
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is the length of the linked list.
- Space Complexity: O(1).
