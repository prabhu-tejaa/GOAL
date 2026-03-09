# Java Fundamentals - Loops, Conditionals, Operators

## 1. Loops

### 1.1 Traditional for Loop

**Syntax:**
```java
for (int i = 0; i < n; i++) {
    // Do something with i
}
```

**Breakdown:**
- `int i = 0` → Initialize counter at 0
- `i < n` → Continue while i is less than n
- `i++` → Increment i by 1 after each iteration

**Example with Array:**
```java
int[] arr = {10, 20, 30, 40, 50};

for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);  // Prints: 10, 20, 30, 40, 50
}
```

**Example with String:**
```java
String s = "hello";

for (int i = 0; i < s.length(); i++) {
    System.out.println(s.charAt(i));  // Prints: h, e, l, l, o
}
```

**When to use:** When you need index access or need to control loop step

---

### 1.2 Enhanced for Loop (for-each Loop)

**Syntax:**
```java
for (DataType variable : collection) {
    // Do something with variable
}
```

**Breakdown:**
- `DataType` = type of elements in collection
- `variable` = gets each element one by one
- `collection` = array, String, ArrayList, etc.

**Example with Array:**
```java
int[] arr = {10, 20, 30, 40, 50};

for (int num : arr) {
    System.out.println(num);  // Prints: 10, 20, 30, 40, 50
}
```

**Example with String (using toCharArray):**
```java
String s = "hello";

for (char c : s.toCharArray()) {
    System.out.println(c);  // Prints: h, e, l, l, o
}
```

**Example with ArrayList:**
```java
ArrayList<Integer> list = new ArrayList<>();
list.add(5);
list.add(10);
list.add(15);

for (int num : list) {
    System.out.println(num);  // Prints: 5, 10, 15
}
```

**When to use:** When you DON'T need the index, just the values. Cleaner code.

**Key difference from traditional for:**
- Can't access index
- Can't modify loop variable to control steps
- Simpler and more readable

---

### 1.3 while Loop

**Syntax:**
```java
while (condition) {
    // Do something
    // Update condition
}
```

**Example:**
```java
int i = 0;
while (i < 5) {
    System.out.println(i);  // Prints: 0, 1, 2, 3, 4
    i++;
}
```

**Example with Array:**
```java
int[] arr = {10, 20, 30, 40, 50};
int i = 0;

while (i < arr.length) {
    System.out.println(arr[i]);
    i++;
}
```

**Example with Two Pointers (DSA Pattern):**
```java
int left = 0, right = arr.length - 1;

while (left < right) {
    System.out.println(arr[left] + " " + arr[right]);
    left++;
    right--;
}
```

**When to use:** When you don't know how many iterations you need (depends on condition)

---

### 1.4 do-while Loop

**Syntax:**
```java
do {
    // Do something
    // Update condition
} while (condition);
```

**Difference:** Executes at least once, then checks condition

**Example:**
```java
int i = 0;
do {
    System.out.println(i);  // Prints: 0, 1, 2, 3, 4
    i++;
} while (i < 5);
```

**When to use:** Rarely in DSA. Use when you must execute at least once.

---

### 1.5 Loop Control Statements

**break** - Exit loop immediately
```java
for (int i = 0; i < 10; i++) {
    if (i == 5) break;  // Exit when i = 5
    System.out.println(i);  // Prints: 0, 1, 2, 3, 4
}
```

**continue** - Skip current iteration, go to next
```java
for (int i = 0; i < 5; i++) {
    if (i == 2) continue;  // Skip when i = 2
    System.out.println(i);  // Prints: 0, 1, 3, 4
}
```

---

## 2. Conditionals

### 2.1 if Statement

**Syntax:**
```java
if (condition) {
    // Execute if condition is true
}
```

**Example:**
```java
int age = 18;
if (age >= 18) {
    System.out.println("Adult");  // Prints: Adult
}
```

**With Array:**
```java
int[] arr = {5, 10, 15};
if (arr.length > 0) {
    System.out.println("Array has elements");
}
```

---

### 2.2 if-else Statement

**Syntax:**
```java
if (condition) {
    // Execute if true
} else {
    // Execute if false
}
```

**Example:**
```java
int num = 7;
if (num % 2 == 0) {
    System.out.println("Even");
} else {
    System.out.println("Odd");  // Prints: Odd
}
```

---

### 2.3 if-else if-else Statement

**Syntax:**
```java
if (condition1) {
    // Execute if condition1 is true
} else if (condition2) {
    // Execute if condition2 is true
} else {
    // Execute if all above are false
}
```

**Example:**
```java
int score = 75;
if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
} else if (score >= 70) {
    System.out.println("C");  // Prints: C
} else {
    System.out.println("F");
}
```

---

### 2.4 Ternary Operator (Conditional Expression)

**Syntax:**
```java
condition ? valueIfTrue : valueIfFalse
```

**Example:**
```java
int age = 15;
String status = age >= 18 ? "Adult" : "Minor";
System.out.println(status);  // Prints: Minor
```

**Useful for concise code:**
```java
int max = a > b ? a : b;  // Get maximum of a and b
```

---

## 3. Comparison Operators

### 3.1 Equality Operators

**`==` (equal to)**
```java
int a = 5;
int b = 5;
System.out.println(a == b);  // Prints: true
```

**`!=` (not equal to)**
```java
int a = 5;
int b = 10;
System.out.println(a != b);  // Prints: true
```

**⚠️ IMPORTANT: String Comparison**
```java
String s = "hello";
String t = "hello";

s == t;          // ❌ WRONG - compares memory addresses (might be false)
s.equals(t);     // ✓ CORRECT - compares content (true)
```

---

### 3.2 Relational Operators

**`<` (less than)**
```java
5 < 10;  // true
```

**`>` (greater than)**
```java
10 > 5;  // true
```

**`<=` (less than or equal to)**
```java
5 <= 5;  // true
```

**`>=` (greater than or equal to)**
```java
10 >= 10;  // true
```

---

## 4. Logical Operators

### 4.1 AND (`&&`)

**Both conditions must be true**
```java
int age = 20;
boolean hasLicense = true;

if (age >= 18 && hasLicense) {
    System.out.println("Can drive");  // Prints: Can drive
}
```

**With Array:**
```java
int[] arr = {1, 2, 3};
if (arr.length > 0 && arr[0] == 1) {
    System.out.println("Valid");
}
```

---

### 4.2 OR (`||`)

**At least one condition must be true**
```java
int age = 15;
boolean hasPermission = true;

if (age >= 18 || hasPermission) {
    System.out.println("Can enter");  // Prints: Can enter
}
```

---

### 4.3 NOT (`!`)

**Negates condition**
```java
boolean isRaining = false;

if (!isRaining) {
    System.out.println("Go outside");  // Prints: Go outside
}
```

**With Methods:**
```java
String s = "hello";
if (!s.isEmpty()) {
    System.out.println("String has content");
}
```

---

## 5. Common DSA Patterns with Loops and Conditionals

### Pattern 1: Loop Through Array and Check Condition

**Traditional for:**
```java
int[] arr = {5, 10, 15, 20, 25};

for (int i = 0; i < arr.length; i++) {
    if (arr[i] > 12) {
        System.out.println(arr[i]);  // Prints: 15, 20, 25
    }
}
```

**Enhanced for:**
```java
int[] arr = {5, 10, 15, 20, 25};

for (int num : arr) {
    if (num > 12) {
        System.out.println(num);  // Prints: 15, 20, 25
    }
}
```

---

### Pattern 2: Two Pointers with while Loop

```java
int[] arr = {1, 2, 3, 4, 5};
int left = 0, right = arr.length - 1;

while (left < right) {
    System.out.println(arr[left] + " " + arr[right]);
    left++;
    right--;
}
// Prints: 1 5, 2 4, 3 3
```

---

### Pattern 3: Loop Through String

**Traditional for:**
```java
String s = "hello";

for (int i = 0; i < s.length(); i++) {
    char c = s.charAt(i);
    if (c == 'l') {
        System.out.println("Found 'l' at index " + i);
    }
}
```

**Enhanced for:**
```java
String s = "hello";

for (char c : s.toCharArray()) {
    if (c == 'l') {
        System.out.println("Found 'l'");
    }
}
```

---

### Pattern 4: Loop Through ArrayList

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(5);
list.add(10);
list.add(15);

for (int num : list) {
    if (num >= 10) {
        System.out.println(num);  // Prints: 10, 15
    }
}
```

---

### Pattern 5: Loop Through HashMap

```java
HashMap<Character, Integer> map = new HashMap<>();
map.put('a', 1);
map.put('b', 2);
map.put('c', 3);

for (Character key : map.keySet()) {
    System.out.println(key + " -> " + map.get(key));
}

// Or with entrySet (more efficient):
for (Map.Entry<Character, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

---

### Pattern 6: Frequency Array with Loops

```java
String s = "hello";
int[] freq = new int[26];

// Count frequencies
for (char c : s.toCharArray()) {
    freq[c - 'a']++;
}

// Check frequencies
for (int i = 0; i < 26; i++) {
    if (freq[i] > 0) {
        System.out.println((char)('a' + i) + " appears " + freq[i] + " times");
    }
}
```

---

## 6. Quick Reference Table

| Need | Syntax | Example |
|------|--------|---------|
| Loop with index | `for (int i = 0; i < n; i++)` | Access arr[i] |
| Loop values only | `for (type var : collection)` | for (int num : arr) |
| Loop unknown times | `while (condition)` | Two pointers |
| Simple check | `if (condition)` | if (age > 18) |
| Two options | `if-else` | if-else |
| Multiple options | `if-else if-else` | score grades |
| Quick assignment | `condition ? a : b` | max = a > b ? a : b |
| Equal values | `==` (for primitives) | if (a == 5) |
| Equal strings | `.equals()` | if (s.equals(t)) |
| AND condition | `&&` | if (a > 0 && b < 10) |
| OR condition | `\|\|` | if (x == 5 \|\| x == 10) |
| NOT condition | `!` | if (!flag) |

---

## 7. Common Mistakes to Avoid

❌ **Using `==` for String comparison**
```java
String s = "hello";
if (s == "hello") { }  // ❌ WRONG
if (s.equals("hello")) { }  // ✓ CORRECT
```

❌ **Infinite loop**
```java
while (true) {
    // Never breaks, infinite loop
}
```

❌ **Off-by-one in loop**
```java
int[] arr = {1, 2, 3};
for (int i = 0; i <= arr.length; i++) {  // ❌ Will cause error at arr[3]
    System.out.println(arr[i]);
}
// ✓ Should be: i < arr.length
```

❌ **Modifying loop variable in enhanced for**
```java
int[] arr = {1, 2, 3};
for (int num : arr) {
    num = 10;  // ❌ Doesn't modify arr, only local variable
}
```

❌ **Not breaking out of loop when needed**
```java
for (int i = 0; i < 10; i++) {
    if (arr[i] == target) {
        // ❌ Should break here instead of continuing
        System.out.println("Found!");
    }
}
```

---

## 8. Cheat Sheet

**Array Loop:**
```java
for (int i = 0; i < arr.length; i++) { }  // With index
for (int num : arr) { }                     // Values only
```

**String Loop:**
```java
for (int i = 0; i < s.length(); i++) { char c = s.charAt(i); }  // With index
for (char c : s.toCharArray()) { }                               // Values only
```

**ArrayList Loop:**
```java
for (int i = 0; i < list.size(); i++) { int val = list.get(i); }  // With index
for (int num : list) { }                                            // Values only
```

**HashMap Loop:**
```java
for (Character key : map.keySet()) { }
for (Map.Entry<Character, Integer> entry : map.entrySet()) { }
```

**Two Pointer Pattern:**
```java
int left = 0, right = n - 1;
while (left < right) {
    // Process arr[left] and arr[right]
    left++;
    right--;
}
```

**Frequency Array Pattern:**
```java
int[] freq = new int[26];
for (char c : s.toCharArray()) {
    freq[c - 'a']++;
}
```
