# Validate Subsequence

## Problem

Given two non-empty arrays of integers, write a function that determines whether the second array is a subsequence of the first one.

A subsequence of an array is a set of numbers that aren't necessarily adjacent in the array but that are in the same order as they appear in the array. For instance, the numbers `[1, 3, 4]` form a subsequence of the array `[1, 2, 3, 4]`, and so do the numbers `[2, 4]`. Note that a single number in an array and the array itself are both valid subsequences of the array.

Sample Input

```
array = [5, 1, 22, 25, 6, -1, 8, 10]
sequence = [1, 6, -1, 10]
```

Sample Output

```
true
```

#

## Approach 1: Array Single Scan

```JAVA
import java.util.List;

class Program {
  /**
  * Approach 1: Array Single Scan
  *
  * Time Complexity: O(N), where N is the length of the input array.
  * Space Complexity: O(1).
  *
  * @param array  input array of size N.
  * @param sequence  sequence array of size M.
  */
  public static boolean isValidSubsequence(List<Integer> array, List<Integer> sequence) {
    int sequencePtr = 0;
    for(Integer arrayEle: array){
      if(arrayEle == sequence.get(sequencePtr)){
        sequencePtr++;
        if(sequencePtr == sequence.size()){
          return true;
        }
      }
    }
    return false;
  }
}


```

### Complexity Analysis

- Time Complexity: O(N), where N is the length of the input array.
- Space Complexity: O(1).
