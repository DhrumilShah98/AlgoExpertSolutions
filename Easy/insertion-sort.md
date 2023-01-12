# Insertion Sort

## Problem

Write a function that takes in an array of integers and returns a sorted version of that array. Use the Insertion Sort algorithm to sort the array.

Sample Input

```
array = [8, 5, 2, 9, 5, 6, 3]
```

Sample Output

```
[2, 3, 5, 5, 6, 8, 9]
```

Hint: Divide the input array into two subarrays in place. The first subarray should be sorted at all times and should start with a length of 1, while the second subarray should be unsorted. Iterate through the unsorted subarray, inserting all of its elements into the sorted subarray in the correct position by swapping them into place. Eventually, the entire array will be sorted.

#

## Approach 1: Brute Force (Two loops)

```JAVA
class Program {
  /**
  * Approach 1: Brute Force (Two loops)
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
  public static int[] insertionSort(int[] array) {
    for(int i = 1; i < array.length; ++i){
      int j = i;
      while(j > 0 && array[j] < array[j - 1]){
        int temp = array[j];
        array[j] = array[j - 1];
        array[j - 1] = temp;
        j--;
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
