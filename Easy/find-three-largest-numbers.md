# Find Three Largest Numbers

## Problem

Write a function that takes in an array of at least three integers and, without sorting the input array, returns a sorted array of the three largest integers in the input array.

The function should return duplicate integers if necessary; for example, it should return `[10, 10, 12]` for an input array of `[10, 5, 9, 10, 12]`.

Sample Input

```
array = [141, 1, 17, -7, -17, -27, 18, 541, 8, 7, 7]
```

Sample Output

```
[18, 141, 541]
```

#

## Approach 1: Iterative Approach

```JAVA
class Program {

  /**
  * Approach 1: Iterative Approach
  *
  * Time Complexity: O(N), where N is the length of the input array.
  * Space Complexity: O(1).
  *
  * @param array  input array of size N.
  */
  public static int[] findThreeLargestNumbers(int[] array) {
    int[] sortedThreeLargest = new int[]{Integer.MIN_VALUE, Integer.MIN_VALUE, Integer.MIN_VALUE};
    for(int i = 0; i < array.length; ++i) {
      int num = array[i];
      if(num > sortedThreeLargest[0]) sortedThreeLargest[0] = num;
      if(sortedThreeLargest[0] > sortedThreeLargest[1]) swap(0, 1, sortedThreeLargest);
      if(sortedThreeLargest[1] > sortedThreeLargest[2]) swap(1, 2, sortedThreeLargest);
    }
    return sortedThreeLargest;
  }

  private static void swap(int index1, int index2, int[] array) {
    int temp = array[index1];
    array[index1] = array[index2];
    array[index2] = temp;
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is the length of the input array.
- Space Complexity: O(1).
