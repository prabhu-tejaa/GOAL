# Java Strings - DSA Interview Guide

## 1. What is a String?

A **String** is a sequence of characters. It's an **immutable object** in Java (once created, cannot be changed).

```java
String s = "hello";  // Creates a String object with 5 characters
```

**Immutable means:** If you modify a string, a NEW string is created. The original stays unchanged.

```java
String s = "hello";
s = s + " world";  // Creates NEW string "hello world", old "hello" still exists (garbage collected)
```

---

## 2. String Initialization

### Method 1: String Literal (Most Common)

```java
String s = "hello";
```

- Stored in **String pool** (special memory area for efficiency)
- Fastest way to create strings
- **Use this in interviews**

### Method 2: Using new Keyword

```java
String s = new String("hello");
```

- Creates object on heap
- Less efficient
- Rarely needed in interviews
- **Avoid this**

### Method 3: From Character Array

```java
char[] chars = {'h', 'e', 'l', 'l', 'o'};
String s = new String(chars);
```

- Converts char array to string
- Useful when building strings dynamically

---

## 3. Memory & Immutability

### How String is Stored

```
String s = "hello";

Heap Memory:
┌─────────────┐
│   String    │
│  object     │
├─────────────┤
│ value: h    │
│       e     │
│       l     │
│       l     │
│       o     │
└─────────────┘
```

**Each character = 2 bytes (Java uses UTF-16 encoding)**

Total for "hello" = 5 chars × 2 bytes = 10 bytes + object overhead (~40-50 bytes) = ~50-60 bytes

### Why Immutable?

- Safer (can't accidentally change)
- Allows String pooling (multiple references to same string = memory efficient)
- Thread-safe

---

## 4. Core String Operations

### 1. `length()` - Get String Length

```java
String s = "hello";
int len = s.length();  // Returns 5
```

- **Time: O(1)** (returns a stored field)
- **Returns: int**
- Works on any string

### 2. `charAt(index)` - Get Character at Index

```java
String s = "hello";
char c = s.charAt(0);   // Returns 'h'
char c = s.charAt(4);   // Returns 'o'
char c = s.charAt(10);  // ERROR: StringIndexOutOfBoundsException
```

- **Time: O(1)** (direct index access)
- **Returns: char**
- Index from 0 to length()-1
- **Throws exception if index out of bounds**

### 3. `toCharArray()` - Convert to Character Array

```java
String s = "hello";
char[] chars = s.toCharArray();  // Returns ['h', 'e', 'l', 'l', 'o']
```

- **Time: O(n)** (copies all characters)
- **Returns: char[]**
- Creates NEW array (original string unchanged)
- **Used in DSA:** Loop through string character by character

```java
for (char c : s.toCharArray()) {
    System.out.println(c);  // Prints: h, e, l, l, o
}
```

### 4. `substring(startIndex, endIndex)` - Extract Portion

```java
String s = "hello";
String sub = s.substring(0, 3);   // Returns "hel" (index 0,1,2 — excludes 3)
String sub = s.substring(2);      // Returns "llo" (from index 2 to end)
String sub = s.substring(0, 0);   // Returns "" (empty string)
```

- **Time: O(n)** (copies characters to new string)
- **Returns: String**
- Range: [startIndex, endIndex) — includes start, excludes end
- **Common mistake:** Forgetting it excludes endIndex

### 5. `equals(otherString)` - Compare Strings

```java
String s = "hello";
String t = "hello";
String u = "world";

s.equals(t);   // Returns true (same content)
s.equals(u);   // Returns false (different content)
```

- **Time: O(n)** (compares each character)
- **Returns: boolean**
- **Use this for string comparison** (not ==)

### 6. `equalsIgnoreCase(otherString)` - Case-Insensitive Compare

```java
String s = "Hello";
String t = "hello";

s.equals(t);              // Returns false (case-sensitive)
s.equalsIgnoreCase(t);    // Returns true (ignores case)
```

- **Time: O(n)**
- **Returns: boolean**

### 7. `indexOf(char/String)` - Find First Occurrence

```java
String s = "hello";

s.indexOf('l');      // Returns 2 (first 'l' is at index 2)
s.indexOf('x');      // Returns -1 (not found)
s.indexOf("ll");     // Returns 2 (substring starts at index 2)
```

- **Time: O(n)** (scans through string)
- **Returns: int** (index of first occurrence, -1 if not found)

### 8. `contains(String)` - Check if Contains Substring

```java
String s = "hello";

s.contains("ell");   // Returns true
s.contains("xyz");   // Returns false
```

- **Time: O(n)** (scans through string)
- **Returns: boolean**

### 9. `startsWith(String)` / `endsWith(String)` - Check Beginning/End

```java
String s = "hello";

s.startsWith("hel");  // Returns true
s.endsWith("lo");     // Returns true
s.startsWith("world"); // Returns false
```

- **Time: O(n)** (scans characters)
- **Returns: boolean**

### 10. `toUpperCase()` / `toLowerCase()` - Case Conversion

```java
String s = "Hello";

s.toUpperCase();   // Returns "HELLO"
s.toLowerCase();   // Returns "hello"
```

- **Time: O(n)** (creates new string with converted characters)
- **Returns: String** (new string, original unchanged)
- Immutable: original `s` is still "Hello"

### 11. `trim()` - Remove Leading/Trailing Whitespace

```java
String s = "  hello world  ";

s.trim();   // Returns "hello world" (spaces removed)
```

- **Time: O(n)**
- **Returns: String** (new string)

### 12. `split(delimiter)` - Split into Array

```java
String s = "apple,banana,orange";

String[] fruits = s.split(",");  // Returns ["apple", "banana", "orange"]
```

- **Time: O(n)** (scans and splits)
- **Returns: String[]** (array of substrings)
- **Delimiter** = separator character(s)

### 13. `replace(oldChar, newChar)` - Replace Characters

```java
String s = "hello";

s.replace('l', 'x');   // Returns "hexxo"
```

- **Time: O(n)**
- **Returns: String** (new string)
- Original unchanged

---

## 5. String vs StringBuilder vs StringBuffer

### String (Immutable)

```java
String s = "hello";
s = s + " world";  // Creates NEW string, old one garbage collected
```

- **Time for concatenation: O(n)**
- Use when: String content doesn't change much

### StringBuilder (Mutable)

```java
StringBuilder sb = new StringBuilder("hello");
sb.append(" world");  // Modifies existing object
String result = sb.toString();
```

- **Time for append: O(1) amortized**
- Use when: Building strings in loops (more efficient)
- **For DSA:** Use this when you need to concatenate many times

### StringBuffer (Thread-Safe, Slower)

```java
StringBuffer sb = new StringBuffer("hello");
sb.append(" world");
```

- Same as StringBuilder but synchronized (thread-safe)
- **Slower** than StringBuilder
- Rarely used in interviews

**Interview answer:** "For building strings, I'd use StringBuilder for efficiency."

---

## 6. Character Conversion (Important for DSA)

### char to int

```java
char c = '5';
int digit = c - '0';  // Returns 5

char c = 'a';
int index = c - 'a';  // Returns 0 (for lowercase)
```

### int to char

```java
int digit = 5;
char c = '0' + digit;  // Returns '5'

int index = 0;
char c = 'a' + index;  // Returns 'a'
```

### Character Class Methods

```java
Character.isDigit('5');      // Returns true
Character.isLetter('a');     // Returns true
Character.isLetterOrDigit('b') // Returns true
Character.isUpperCase('A');  // Returns true
Character.isLowerCase('a');  // Returns true
Character.toLowerCase('A');  // Returns 'a'
Character.toUpperCase('a');  // Returns 'A'
```

---

## 7. Common DSA String Patterns

### Pattern 1: Loop Through Each Character

```java
String s = "hello";
for (char c : s.toCharArray()) {
    // Process each character
}
```

### Pattern 2: Build String Dynamically

```java
StringBuilder result = new StringBuilder();
for (char c : s.toCharArray()) {
    if (condition) {
        result.append(c);
    }
}
return result.toString();
```

### Pattern 3: Check Character Frequency

```java
String s = "hello";
int[] freq = new int[26];  // For lowercase letters
for (char c : s.toCharArray()) {
    freq[c - 'a']++;
}
```

### Pattern 4: Two-String Comparison

```java
String s = "abc";
String t = "def";

if (s.length() != t.length()) return false;
if (s.equals(t)) return true;
```

---

## 8. Time Complexity Reference

|Operation|Time|Space|Notes|
|---|---|---|---|
|length()|O(1)|—|Field lookup|
|charAt(i)|O(1)|—|Direct access|
|toCharArray()|O(n)|O(n)|Creates new array|
|substring()|O(n)|O(n)|Creates new string|
|equals()|O(n)|—|Character comparison|
|indexOf()|O(n)|—|Linear search|
|split()|O(n)|O(n)|Creates new array|
|concat/+|O(n)|O(n)|Creates new string|
|toLowerCase()|O(n)|O(n)|Creates new string|

---

## 9. Interview Red Flags

❌ **Don't use `==` to compare strings**

```java
String s = "hello";
String t = "hello";
if (s == t) { }  // ❌ Compares memory addresses, not content
if (s.equals(t)) { }  // ✓ Compares actual content
```

❌ **Don't forget String is immutable**

```java
String s = "hello";
s.toUpperCase();  // Creates NEW string, doesn't modify s
s = s.toUpperCase();  // ✓ Assign back to s
```

❌ **Don't loop with String concatenation**

```java
String result = "";
for (int i = 0; i < n; i++) {
    result = result + "a";  // ❌ Creates O(n) new strings = O(n²) time
}

// ✓ Use StringBuilder instead
StringBuilder result = new StringBuilder();
for (int i = 0; i < n; i++) {
    result.append("a");  // O(1) amortized
}
```

❌ **Don't forget charAt() bounds**

```java
String s = "hello";
s.charAt(10);  // ❌ Throws StringIndexOutOfBoundsException
```

---

## 10. Quick Reference Table

|Need|Use|Time|
|---|---|---|
|Get length|`s.length()`|O(1)|
|Get character at index|`s.charAt(i)`|O(1)|
|Loop through characters|`for (char c : s.toCharArray())`|O(n)|
|Extract substring|`s.substring(start, end)`|O(n)|
|Check equality|`s.equals(t)`|O(n)|
|Find substring position|`s.indexOf("sub")`|O(n)|
|Check if contains|`s.contains("sub")`|O(n)|
|Case conversion|`s.toLowerCase()`|O(n)|
|Remove spaces|`s.trim()`|O(n)|
|Build string dynamically|`StringBuilder.append()`|O(1) amortized|

---

## 11. String Interview Questions Pattern

**Q: How do you compare two strings?** A: Use `equals()` for content comparison, not `==`. `==` compares memory addresses.

**Q: Is String mutable?** A: No, String is immutable. Each modification creates a new String object.

**Q: When to use StringBuilder?** A: When building strings in loops or concatenating many times. It's more efficient than String concatenation.

**Q: What's the time complexity of string operations?** A: Most are O(n) because they scan the entire string (length, substring, equals, indexOf). charAt() is O(1).

---

## 12. Key Takeaways

✓ Use String for fixed content ✓ Use StringBuilder for dynamic building ✓ Use `equals()` not `==` for comparison ✓ Remember: charAt() is O(1), substring() is O(n) ✓ toCharArray() is your friend in DSA ✓ Immutability means every modification creates new object ✓ char - 'a' converts to index for frequency arrays