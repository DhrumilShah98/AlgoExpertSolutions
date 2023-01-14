# Palindrome Check

## Problem

Write a function that takes in a non-empty string and that returns a boolean representing whether the string is a palindrome.

A palindrome is defined as a string that's written the same forward and backward. Note that single-character strings are palindromes.

Sample Input

```
string = "abcdcba"
```

Sample Output

```
true //it's written the same forward and backward
```

#

## Approach 1: Brute Force (For loop with string concatenation)

```JAVA
class Program {
  /**
  * Approach 1: Brute Force (For loop with string concatenation)
  *
  * Time Complexity: O(N^2), where N is the length of the input string.
  * Space Complexity: O(N), where N is the length of the input string.
  *
  * @param str  input string of length N.
  */
  public static boolean isPalindrome(String str) {
    String revStr = "";
    for(int i = str.length() - 1; i >= 0; i--){
      revStr += str.charAt(i);
    }
    return revStr.equals(str);
  }
}

```

### Complexity Analysis

- Time Complexity: O(N^2), where N is the length of the input string.
  - The reason for O(N^2) time complexity is that in Java strings are immutable, and as a result, each time we append to the string, a new string object is created. The loop in the code does 1 + 2 + 3 + ... + N = N \* (N + 1) / 2 = O(N^2) operations.
- Space Complexity: O(N), where N is length of the input string.

### Specific to Java

- To avoid O(N^2) time complexity, we can use `StringBuilder` class instead of `String` class. `StringBuilder` in Java is mutable and therefor it helps us to acheive O(N) time complexity. However, space complexity is still O(N). Below is the code that uses `StringBuilder` class available in Java.

```JAVA
class Program {
  /**
  *
  * Time Complexity: O(N), where N is the length of the input string.
  * Space Complexity: O(N), where N is the length of the input string.
  *
  * @param str  input string of length N.
  */
  public static boolean isPalindrome(String str) {
    StringBuilder revStrBuilder = new StringBuilder();
    for(int i = str.length() - 1; i >= 0; i--){
      revStrBuilder.append(str.charAt(i));
    }
    return revStrBuilder.toString().equals(str);
  }
}

```

## Approach 2: Recursive Approach

```JAVA
class Program {
  /**
  * Approach 2: Recursive Approach
  *
  * Time Complexity: O(N), where N is the length of the input string.
  * Space Complexity: O(N), where N is the length of the input string.
  *
  * @param str  input string of length N.
  */
  public static boolean isPalindrome(String str) {
    int leftPtr = 0;
    int rightPtr = str.length() - 1;
    return checkPalindrome(leftPtr, rightPtr, str);
  }

  private static boolean checkPalindrome(int leftPtr, int rightPtr, String str){
    if(leftPtr >= rightPtr){
      return true;
    }
    return checkPalindrome(leftPtr + 1, rightPtr - 1, str) && (str.charAt(leftPtr) == str.charAt(rightPtr));
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is the length of the input string.
- Space Complexity: O(N), where N is the length of the input string.

#

## Approach 3: Two Pointer Iterative Approach

```JAVA
class Program {
  /**
  * Approach 3: Two Pointer Iterative Approach
  *
  * Time Complexity: O(N), where N is the length of the input string.
  * Space Complexity: O(1), where N is the length of the input string.
  *
  * @param str  input string of length N.
  */
  public static boolean isPalindrome(String str) {
    int leftPtr = 0;
    int rightPtr = str.length() - 1;
    while(leftPtr < rightPtr) {
      if(str.charAt(leftPtr) != str.charAt(rightPtr)) {
        return false;
      }
      leftPtr++;
      rightPtr--;
    }
    return true;
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is the length of the input string.
- Space Complexity: O(1).
