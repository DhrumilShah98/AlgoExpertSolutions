# Binary Search

## Problem

Write a function that takes in a sorted array of integers as well as a target integer. The function should use the Binary Search algorithm to determine if the target integer is contained in the array and should return its index if it is, otherwise `-1`.

Sample Input

```
array = [0, 1, 21, 33, 45, 45, 61, 71, 72, 73]
target = 33
```

Sample Output

```
3
```

#

## Approach 1: Recursive Approach

```JAVA
class Program {
  /**
  * Approach 1: Recursive Approach
  *
  * Time Complexity: O(logN), where N is the length of the input array.
  * Space Complexity: O(logN), where N is the length of the input array.
  *
  * @param array  input array of size N.
  * @param target  element to be found in the array.
  */
  public static int binarySearch(int[] array, int target) {
    int leftPtr = 0;
    int rightPtr = array.length - 1;
    return findElement(leftPtr, rightPtr, array, target);
  }

  private static int findElement(int leftPtr, int rightPtr, int[] array, int target) {
    if(leftPtr > rightPtr) {
      return -1;
    }
    int mid = (rightPtr + leftPtr)/2;
    if (target < array[mid]) {
      return findElement(leftPtr, mid - 1, array, target);
    } else if (target > array[mid]) {
      return findElement(mid + 1, rightPtr, array, target);
    } else {
      return mid;
    }
  }
}

```

### Complexity Analysis

- Time Complexity: O(logN), where N is the length of the input array.
- Space Complexity: O(logN), where N is the length of the input array.

#

## Approach 2: Iterative Approach

```JAVA
class Program {
  /**
  * Approach 2: Iterative Approach
  *
  * Time Complexity: O(logN), where N is the length of the input array.
  * Space Complexity: O(1).
  *
  * @param array  input array of size N.
  * @param target  element to be found in the array.
  */
  public static int binarySearch(int[] array, int target) {
    int leftPtr = 0;
    int rightPtr = array.length - 1;
    return findElement(leftPtr, rightPtr, array, target);
  }

  private static int findElement(int leftPtr, int rightPtr, int[] array, int target) {
    while(leftPtr <= rightPtr){
      int mid = (rightPtr + leftPtr)/2;
      if (target < array[mid]) {
        rightPtr = mid - 1;
      } else if (target > array[mid]) {
        leftPtr = mid + 1;
      } else {
        return mid;
      }
    }
    return -1;
  }
}

```

### Complexity Analysis

- Time Complexity: O(logN), where N is the length of the input array.
- Space Complexity: O(1).
