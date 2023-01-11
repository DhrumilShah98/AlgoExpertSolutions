# Two Number Sum

## Problem

Write a function that takes in a non-empty array of distinct integers and an integer representing a target sum. If any two numbers in the input array sum up to the target sum, the function should return them in an array, in any order. If no two numbers sum up to the target sum, the function should return an empty array.

Note that the target sum has to be obtained by summing two different integers in the array; you can't add a single integer to itself in order to obtain the target sum.

You can assume that there will be at most one pair of numbers summing up to the target sum.

Sample Input

```
array = [3, 5, -4, 8, 11, 1, -1, 6]
targetSum = 10
```

Sample Output

```
[-1, 11] // the numbers could be in reverse order
```

#

## Approach 1: Brute Force (Two for loops)

```JAVA
class Program {
  /**
  * Approach 1: Brute Force (Two for loops)
  *
  * Time Complexity: O(N^2), where N is the length of the input array.
  * Space Complexity: O(1).
  *
  * @param array  input array of size N.
  * @param targetSum  target sum to achieve.
  */
  public static int[] twoNumberSum(int[] array, int targetSum) {
    int num1, num2, result;
    for(int i = 0; i < array.length - 1; ++i){
      num1 = array[i];
      for(int j = i + 1; j < array.length; ++j){
        num2 = array[j];
        result = num1 + num2;
        if(result == targetSum){
          return new int[]{num1, num2};
        }
      }
    }
    return new int[0];
  }
}

```

### Complexity Analysis

- Time Complexity: O(N^2), where N is the length of the input array.
- Space Complexity: O(1).

#

## Approach 2: One Pass with Hash Table

```JAVA
import java.util.HashSet;

class Program {
  /**
  * Approach 2: One Pass with Hash Table
  *
  * Time Complexity: O(N), where N is the length of the input array.
  * Space Complexity: O(N), where N is the length of the input array.
  *
  * @param array  input array of size N.
  * @param targetSum  target sum to achieve.
  */
  public static int[] twoNumberSum(int[] array, int targetSum) {
    HashSet<Integer> numsEncounteredInArray = new HashSet<Integer>();
    int currentNum, diff;
    for(int i = 0; i < array.length; ++i){
      currentNum = array[i];
      diff = targetSum - currentNum;
      if(numsEncounteredInArray.contains(diff)){
        return new int[]{currentNum, diff};
      } else {
        numsEncounteredInArray.add(currentNum);
      }
    }
    return new int[0];
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is the length of the input array.
- Space Complexity: O(N), where N is the length of the input array.

#

## Approach 3: Sort + Two Pointers

```JAVA
import java.util.Arrays;

class Program {
  /**
  * Approach 3: Sort + Two Pointers
  *
  * Time Complexity: O(N * log(N)), where N is the length of the input array.
  * Space Complexity: O(log(N)) or O(N), depending on the implementation of the sorting algorithm.
  *
  * @param array  input array of size N.
  * @param targetSum  target sum to achieve.
  */
  public static int[] twoNumberSum(int[] array, int targetSum) {
    Arrays.sort(array);
    int leftPtr = 0;
    int rightPtr = array.length - 1;
    int currentSum;
    while(leftPtr < rightPtr){
      currentSum = array[leftPtr] + array[rightPtr];
      if(currentSum > targetSum){
        rightPtr--;
      } else if(currentSum < targetSum){
        leftPtr++;
      } else {
        return new int[]{array[leftPtr], array[rightPtr]};
      }
    }
    return new int[0];
  }
}

```

### Complexity Analysis

- Time Complexity: O(N \* log(N)), where N is the length of the input array.
- Space Complexity: O(log(N)) or O(N), depending on the implementation of the sorting algorithm.
