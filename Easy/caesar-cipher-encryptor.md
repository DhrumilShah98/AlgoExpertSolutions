# Caesar Cipher Encryptor

## Problem

Given a non-empty string of lowercase letters and a non-negative integer representing a key, write a function that returns a new string obtained by shifting every letter in the input string by k positions in the alphabet, where k is the key.

Note that letters should "wrap" around the alphabet; in other words the letter 'z' shifted by one returns the letter 'a'.

Sample Input

```
string = "xyz"
key = 2
```

Sample Output

```
"zab"
```

#

## Approach 1: Iterative Approach

```JAVA
import java.util.Arrays;

class Program {
  /**
  * Approach 1: Iterative Approach
  *
  * Time Complexity: O(N), where N is the length of the input string.
  * Space Complexity: O(N), where N is the length of the input string.
  *
  * @param str  input string of size N.
  * @param key  non-negative integer representing a key.
  */
  public static String caesarCypherEncryptor(String str, int key) {
    char []newStrArr = new char[str.length()];
    key = key % 26;
    for(int i = 0; i < newStrArr.length; ++i){
      newStrArr[i] = shiftCharByKeyPositions(str.charAt(i), key);
    }
    return new String(newStrArr);
  }

  private static char shiftCharByKeyPositions(char c, int key){
    final int MIN_ASCII = 'a'; // 97
    final int MAX_ASCII = 'z'; // 122
    int newCASCII = (int)c + key;
    return (newCASCII <= MAX_ASCII) ? (char)newCASCII : (char)(MIN_ASCII + newCASCII % MAX_ASCII - 1);
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is the length of the input string.
- Space Complexity: O(N), where N is the length of the input string.
