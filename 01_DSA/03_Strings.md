
1. **`s.length()`** = get string length
    - Time: O(1)
    - Returns an integer
2. **`s.toCharArray()`** = convert string to character array
    - Time: O(n)
    - Returns char[]
    - Then you can loop: `for (char c : s.toCharArray())`
3. **`s.charAt(i)`** = get character at index i
    - Time: O(1)
    - Returns single char

| Operation | Code                | Time | What It Returns |
| --------- | ------------------- | ---- | --------------- |
| Length    | `s.length()`        | O(1) | int             |
| To Array  | `s.toCharArray()`   | O(n) | char[]          |
| Get Char  | `s.charAt(0)`       | O(1) | char            |
| Substring | `s.substring(0, 3)` | O(n) | String          |
| Compare   | `s.equals(t)`       | O(n) | boolean         |

## String Initialization in Java

java

```java
String s = "anagram";  // String literal (simplest way)
String t = new String("nagaram");  // Object creation (rarely needed)
```

## Memory It Takes

**String is immutable object in Java.**

When you do: `String s = "anagram"`

- String object created on heap
- 7 characters stored
- Each char = 2 bytes (Java uses UTF-16)
- Total: ~7 × 2 = 14 bytes + object overhead (~40-50 bytes)
- **Total: ~54-64 bytes for "anagram"**

