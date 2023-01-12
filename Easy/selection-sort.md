# Selection Sort

## Problem

Write a function that takes in an array of integers and returns a sorted version of that array. Use the Selection Sort algorithm to sort the array.

Sample Input

```
array = [8, 5, 2, 9, 5, 6, 3]
```

Sample Output

```
[2, 3, 5, 5, 6, 8, 9]
```

Hint: Divide the input array into two subarrays in place. The first subarray should be sorted at all times and should start with a length of 0, while the second subarray should be unsorted. Find the smallest (or largest) element in the unsorted subarray and insert it into the sorted subarray with a swap. Repeat this process of finding the smallest (or largest) element in the unsorted subarray and inserting it in its correct position in the sorted subarray with a swap until the entire array is sorted.

#

## Approach 1: Brute Force (Two for loops)

```JAVA
class Program {
  /**
  * Approach 1: Brute Force (Two for loops)
  *
  * 1. Best Case, Average Case & Worst Case
  *     - Time Complexity: O(N^2), where N is the length of the input array.
  *     - Space Complexity: O(1).
  *
  * @param array  input array of size N.
  */
  public static int[] selectionSort(int[] array) {
    for(int i = 0; i < array.length - 1; ++i){
      int smallestEleIndex = i;
      for(int j = i + 1; j < array.length; ++j){
        if(array[j] < array[smallestEleIndex]){
          smallestEleIndex = j;
        }
      }
      int temp = array[i];
      array[i] = array[smallestEleIndex];
      array[smallestEleIndex] = temp;
     }
    return array;
  }
}

```

### Complexity Analysis

1. Best Case, Average Case & Worst Case
   - Time Complexity: O(N^2), where N is the length of the input array.
   - Space Complexity: O(1).
