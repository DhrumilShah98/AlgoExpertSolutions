# Sorted Squared Array

## Problem

Write a function that takes in a non-empty array of integers that are sorted in ascending order and returns a new array of the same length with the squares of the original integers also sorted in ascending order.

Sample Input

```
array = [1, 2, 3, 5, 6, 8, 9]
```

Sample Output

```
[1, 4, 9, 25, 36, 64, 81]
```

#

## Approach 1: Brute Force + Sort

```JAVA
import java.util.Arrays;

class Program {
  /**
  * Approach 1: Brute Force + Sort
  *
  * Time Complexity: O(N * log(N)), where N is the length of the input array.
  * Space Complexity: O(N), where N is the length of the input array.
  *
  * @param array  input array of size N.
  */
  public int[] sortedSquaredArray(int[] array) {
    int[] newArray = new int[array.length];
    for(int i = 0; i < array.length; ++i){
      newArray[i] = array[i] * array[i];
    }
    Arrays.sort(newArray);
    return newArray;
  }
}


```

### Complexity Analysis

- Time Complexity: O(N \* log(N)), where N is the length of the input array.
- Space Complexity: O(N), where N is the length of the input array.

#

## Approach 2: Two Pointers

```JAVA
class Program {
  /**
  * Approach 2: Two Pointers
  *
  * Time Complexity: O(N), where N is the length of the input array.
  * Space Complexity: O(N), where N is the length of the input array.
  *
  * @param array  input array of size N.
  */
  public int[] sortedSquaredArray(int[] array) {
    int[] newArray = new int[array.length];
    int newArrayIndex = array.length - 1;
    int leftPtr = 0;
    int rightPtr = array.length - 1;
    int num1Sqr, num2Sqr;
    while(leftPtr <= rightPtr){
      num1Sqr = array[leftPtr] * array[leftPtr];
      num2Sqr = array[rightPtr] * array[rightPtr];
      if(num1Sqr >= num2Sqr){
        leftPtr++;
        newArray[newArrayIndex] = num1Sqr;
      } else {
        rightPtr--;
        newArray[newArrayIndex] = num2Sqr;
      }
      newArrayIndex--;
    }
    return newArray;
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is the length of the input array.
- Space Complexity: O(N), where N is the length of the input array.
