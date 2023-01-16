# Nth Fibonacci

## Problem

The Fibonacci sequence is defined as follows: the first number of the sequence is `0`, the second number is `1`, , and the `nth` number is the sum of the `(n - 1)th` and `(n - 2)th` numbers. Write a function that takes in an integer `n` and returns the `nth` Fibonacci number.

Important note: the Fibonacci sequence is often defined with its first two numbers as `F0 = 0` and `F1 = 1`. For the purpose of this question, the first Fibonacci number is `F0`; therefore, `getNthFib(1)` is equal to `F0`, `getNthFib(2)` is equal to `F1`, etc...

Sample Input #1

```
n = 2
```

Sample Output #1

```
1 // 0, 1
```

Sample Input #2

```
n = 6
```

Sample Output #2

```
5 // 0, 1, 1, 2, 3, 5
```

#

## Approach 1: Recursive Approach

```JAVA
class Program {
  /**
  * Approach 1: Recursive Approach
  *
  * Time Complexity: O(2^n), where n is the nth fibonacci number to be found.
  * Space Complexity: O(n), where n is the nth fibonacci number to be found.
  *
  * @param n nth fibonacci number to be found.
  */
  public static int getNthFib(int n) {
    if(n <= 1){
      return 0;
    } else if (n == 2) {
      return 1;
    } else {
      return getNthFib(n - 2) + getNthFib(n - 1);
    }
  }
}

```

### Complexity Analysis

- Time Complexity: O(2^n), where n is the nth fibonacci number to be found.
- Space Complexity: O(n), where n is the nth fibonacci number to be found.

#

## Approach 2: Recursive Approach with Memoization

```JAVA
import java.util.HashMap;

class Program {
  /**
  * Approach 2: Recursive Approach with Memoization
  *
  * Time Complexity: O(n), where n is the nth fibonacci number to be found.
  * Space Complexity: O(n), where n is the nth fibonacci number to be found.
  *
  * @param n nth fibonacci number to be found.
  */
  public static int getNthFib(int n) {
    HashMap<Integer, Integer> memo = new HashMap<>();
    memo.put(1, 0);
    memo.put(2, 1);
    return calNthFibo(n, memo);
  }

  private static int calNthFibo(int n, HashMap<Integer, Integer> memo){
    if(memo.containsKey(n)){
      return memo.get(n);
    }
    int result = calNthFibo(n - 2, memo) + calNthFibo(n - 1, memo);
    memo.put(n, result);
    return result;
  }
}

```

### Complexity Analysis

- Time Complexity: O(n), where n is the nth fibonacci number to be found.
- Space Complexity: O(n), where n is the nth fibonacci number to be found.

#

## Approach 3: Iterative Approach

```JAVA
class Program {
  /**
  * Approach 3: Iterative Approach
  *
  * Time Complexity: O(n), where n is the nth fibonacci number to be found.
  * Space Complexity: O(1).
  *
  * @param n nth fibonacci number to be found.
  */
  public static int getNthFib(int n) {
    if(n <= 1){
      return 0;
    } else if (n == 2) {
      return 1;
    } else {
      int prev2 = 0;
      int prev1 = 1;
      int result = 0;
      for(int i = 3; i <= n; ++i){
        result = prev2 + prev1;
        prev2 = prev1;
        prev1 = result;
      }
      return result;
    }
  }
}

```

### Complexity Analysis

- Time Complexity: O(n), where n is the nth fibonacci number to be found.
- Space Complexity: O(1).
