# Bubble Sort

## Problem

Write a function that takes in an array of integers and returns a sorted version of that array. Use the Bubble Sort algorithm to sort the array.

Sample Input

```
array = [8, 5, 2, 9, 5, 6, 3]
```

Sample Output

```
[2, 3, 5, 5, 6, 8, 9]
```

Hint: Traverse the input array, swapping any two numbers that are out of order and keeping track of any swaps that you make. Once you arrive at the end of the array, check if you have made any swaps; if not, the array is sorted and you are done; otherwise, repeat the steps laid out in this hint until the array is sorted.

#

## Approach 1: Brute Force (Two for loops)

```JAVA
class Program {
  /**
  * Approach 1: Brute Force (Two for loops)
  *
  * 1. Best Case
  *     - Time Complexity: O(N), where N is the length of the input array.
  *     - Space Complexity: O(1).
  * 2. Average Case & Worst Case
  *     - Time Complexity: O(N^2), where N is the length of the input array.
  *     - Space Complexity: O(1).
  *
  * @param array  input array of size N.
  */
  public static int[] bubbleSort(int[] array) {
    for(int i = 0; i < array.length - 1; ++i){
      boolean anySwapsMade = false;
      for(int j = 0; j < array.length - 1 - i; ++j) {
        if(array[j] > array[j + 1]){
          int temp = array[j];
          array[j] = array[j + 1];
          array[j + 1] = temp;
          anySwapsMade = true;
        }
      }
      if(!anySwapsMade) {
        break;
      }
    }
    return array;
  }
}

```

### Complexity Analysis

1. Best Case
   - Time Complexity: O(N), where N is the length of the input array.
   - Space Complexity: O(1).
2. Average Case & Worst Case
   - Time Complexity: O(N^2), where N is the length of the input array.
   - Space Complexity: O(1).
