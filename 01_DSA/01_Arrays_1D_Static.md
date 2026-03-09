
09-03-2026 - 22:00
### **What is a 1D Array?**

A 1D array is a **linear collection of elements** stored in **contiguous memory locations**.
- **`int[]`** = static array (fixed size at creation, cannot grow/shrink)
- **`ArrayList<Integer>`** = dynamic array (resizable, grows as you add elements)

```
Array: [10, 20, 30, 40, 50]
Index:  0   1   2   3   4
```

**Contiguous memory** means that data is stored in one single, unbroken block in your computer's RAM.
Think of it like a **row of houses on a street**: If you have a 5-element array, the computer finds a spot large enough for all five and places them right next to each other (House #1, House #2, House #3, etc.) without any gaps or other data in between.

### **Key Characteristics**
- **No Gaps:** Every element follows the previous one immediately in the memory address sequence.
- **Fixed Order:** If the first element is at address `1000`, and each integer takes 4 bytes, the next element _must_ be at `1004`, then `1008`, and so on.
- **Fast Access:** Because the computer knows exactly how "wide" each element is, it can jump to any specific index (like `array[500]`) instantly using simple math, rather than searching through the whole list.

### **Common Data Type Sizes**

| Data Type         | Size in Bytes    | Analogy                             |
| ----------------- | ---------------- | ----------------------------------- |
| **boolean**       | 1 byte (usually) | A simple On/Off light switch.       |
| **char**          | 1 to 2 bytes     | A single character like 'A' or '$'. |
| **int** (Integer) | **4 bytes**      | A standard whole number.            |
| **float**         | 4 bytes          | A number with a decimal point.      |
| **long**          | 8 bytes          | A very large whole number.          |
| **double**        | 8 bytes          | A high-precision decimal number.    |

### **The Conversion to Bits**

- **1 Byte** = 8 bits.
- **4 Bytes** = 4 * 8 = **32 bits**.

- On a 32-bit system, a pointer is **4 bytes**. 
- On a 64-bit system, a pointer is **8 bytes**.
    
Every "bit" is a tiny switch that can be either 0 or 1 (2 possibilities). So, when you have 32 bits, the number of unique combinations you can make is **2 raised to the power of 32**.

### **The "Power" Calculation**

2^32=4,294,967,296
This means a 4-byte integer can store over **4.29 billion** different values.

### **Why should you care?**
When you are solving a LeetCode problem or designing a system (LLD):
1. **Overflow:** If a problem says the input can be 109, a 4-byte `int` is fine. If the input can be 1012, a 4-byte `int` will **overflow** because 1012 is much larger than 231. You would need a 8-byte `long` (263 range).

### **Declaration in Java**

```java
int[] arr = new int[5];           // Array of size 5, initialized to 0
int[] arr = {10, 20, 30, 40, 50}; // Array with values
```

### **Initialization**

```java
int[] arr = new int[5];  // All elements = 0
arr[0] = 10;             // Set element at index 0
```

### **Index (0-based)**

Arrays in Java use **0-based indexing**:

- First element: arr[0]
- Last element: arr[arr.length - 1]

---

## **2. MEMORY**

### **Contiguous Memory Storage**

Arrays are stored **consecutively** in memory.
**consecutively** means things follow one another in a continuous, unbroken sequence like steps on a ladder or cars in a train.

```
Memory Address:  1000  1004  1008  1012  1016
Array Index:      0     1     2     3     4
Value:           10    20    30    40    50
```

### **Address Calculation**

```
Address of arr[i] = Base Address + (i * size of one element)
Address of arr[2] = 1000 + (2 * 4) = 1008
```

### **Why Access is O(1)**

Because of contiguous memory, you can calculate the address directly. No iteration needed.

```java
arr[2] = 30;  // Direct access in O(1)
              // Computer: Base(1000) + 2*4 = 1008 → fetch value
```

---

## **3. OPERATIONS & TIME COMPLEXITY**

### **Access**

```java
int val = arr[2];  // O(1) - direct address calculation
```

### **Search (Linear)**

```java
for (int i = 0; i < arr.length; i++) {
    if (arr[i] == target) return i;
}
// O(n) - must check each element
```

### **Insert at End**

```java
// arr = [10, 20, 30, null, null]
arr[3] = 40;  // O(1) - just add to next position
```

### **Insert at Middle**

```java
// arr = [10, 20, 30, 40, 50]
// Insert 25 at index 1
// Need to shift: [10, 25, 20, 30, 40]
// O(n) - must shift all elements after insertion point
```

### **Delete at End**

```java
// arr = [10, 20, 30, 40, 50]
// Remove arr[4]
arr[4] = 0;  // O(1) - just remove last element
```

### **Delete at Middle**

```java
// arr = [10, 20, 30, 40, 50]
// Remove arr[1] = 20
// Need to shift: [10, 30, 40, 50, null]
// O(n) - must shift all elements after deletion point
```

### **Sort**

```java
Arrays.sort(arr);  // O(n log n) - Java uses Timsort/Mergesort
```

---

## **Quick Reference Table**

|Operation|Time|Space|Notes|
|---|---|---|---|
|Access arr[i]|O(1)|-|Direct memory calculation|
|Linear search|O(n)|-|Check each element|
|Binary search (sorted)|O(log n)|-|Requires sorted array|
|Insert at end|O(1)|O(1)|Just add to next slot|
|Insert at middle|O(n)|O(1)|Shift elements|
|Delete at end|O(1)|O(1)|Just remove last|
|Delete at middle|O(n)|O(1)|Shift elements|
|Sort|O(n log n)|O(log n) or O(n)|Depends on algorithm|
|Copy array|O(n)|O(n)|Create new array|

---

## **4. COMMON PATTERNS**

### **Pattern 1: Two Pointer**

Two indices moving towards each other from opposite ends.

```java
// Check if array is palindrome
int left = 0, right = arr.length - 1;
while (left < right) {
    if (arr[left] != arr[right]) return false;
    left++;
    right--;
}
return true;
// Time: O(n), Space: O(1)
```

### **Pattern 2: Sliding Window**

Maintain a window of elements and slide it across array.

```java
// Find max sum of subarray of size k
int maxSum = 0, currentSum = 0;
for (int i = 0; i < k; i++) {
    currentSum += arr[i];
}
maxSum = currentSum;

for (int i = k; i < arr.length; i++) {
    currentSum = currentSum - arr[i-k] + arr[i];
    maxSum = Math.max(maxSum, currentSum);
}
// Time: O(n), Space: O(1)
```

### **Pattern 3: Prefix Sum**

Precompute cumulative sums for range queries.

```java
// Build prefix sum array
int[] prefix = new int[arr.length + 1];
for (int i = 0; i < arr.length; i++) {
    prefix[i+1] = prefix[i] + arr[i];
}

// Query sum from index l to r: O(1)
int rangeSum = prefix[r+1] - prefix[l];
// Time to build: O(n), Query: O(1)
```

### **Pattern 4: In-place Modification**

Modify array without using extra space.

```java
// Reverse array in-place
int left = 0, right = arr.length - 1;
while (left < right) {
    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;
    left++;
    right--;
}
// Time: O(n), Space: O(1)
```

### **Pattern 5: Sorting Benefits**

Sort first, then solve problem.

```java
// Two Sum (if return indices not needed)
Arrays.sort(arr);
int left = 0, right = arr.length - 1;
while (left < right) {
    int sum = arr[left] + arr[right];
    if (sum == target) return true;
    else if (sum < target) left++;
    else right--;
}
// Time: O(n log n), Space: O(1) or O(n)
```

---

## **5. JAVA METHODS**

```java
int[] arr = {50, 20, 30, 10, 40};

// Length
arr.length;  // 5 - O(1)

// Sorting
Arrays.sort(arr);  // [10, 20, 30, 40, 50] - O(n log n)

// Binary Search (only works on sorted array)
int index = Arrays.binarySearch(arr, 30);  // 2 - O(log n)

// Fill array with value
Arrays.fill(arr, 0);  // All elements become 0 - O(n)

// Copy array
int[] copy = Arrays.copyOf(arr, arr.length);  // O(n)

// Copy range
int[] copy = Arrays.copyOfRange(arr, 1, 4);  // [20, 30, 40] - O(n)

// System.arraycopy (faster for large arrays)
System.arraycopy(arr, 0, dest, 0, arr.length);  // O(n)

// Compare arrays
Arrays.equals(arr1, arr2);  // true/false - O(n)
```

---

## **6. EDGE CASES**

### **Empty Array**

```java
int[] arr = {};
arr.length;  // 0
// Be careful with division by length
```

### **Single Element**

```java
int[] arr = {5};
// Two pointer would have left >= right immediately
```

### **Duplicates**

```java
int[] arr = {1, 2, 2, 3, 3, 3};
// Common in: remove duplicates, find frequency
```

### **Negative Numbers**

```java
int[] arr = {-5, -2, 0, 3, 4};
// Affects comparison, sorting, searching
```

### **Out of Bounds**

```java
int[] arr = {1, 2, 3};
arr[5];  // ArrayIndexOutOfBoundsException
// Always check: i < arr.length
```

---

## **7. SPACE COMPLEXITY**

### **Array Space**

```java
int[] arr = new int[n];  // O(n) - always takes O(n) space
```

### **Extra Space Solutions**

**O(1) - In-place (optimal)**

```java
// Reverse array
int left = 0, right = arr.length - 1;
while (left < right) {
    // swap - no extra space needed
}
```

**O(n) - Extra array**

```java
// Copy array
int[] copy = new int[arr.length];
for (int i = 0; i < arr.length; i++) {
    copy[i] = arr[i];
}
```

---

## **8. INTERVIEW QUESTIONS**

### **Q1: Why is array access O(1)?**

**Answer:** Because arrays are stored in contiguous memory. To access arr[i], the computer calculates the address directly: `Base Address + (i * element size)`. No iteration needed. Direct calculation = O(1).

---

### **Q2: What's the difference between searching a sorted vs unsorted array?**

**Answer:**

- **Unsorted:** Must use linear search O(n) - check each element
- **Sorted:** Can use binary search O(log n) - eliminate half elements each time

---

### **Q3: Why is inserting at the middle O(n)?**

**Answer:** When you insert at position i, all elements after position i must shift one position right. If array is full, you also need to create a larger array and copy everything. Worst case: shift n elements = O(n).

---

### **Q4: When would you use O(n) space to solve an O(n²) problem?**

**Answer:** When it significantly reduces time complexity or improves readability. Example: Two Sum uses HashMap (O(n) space) to achieve O(n) time instead of O(n²) brute force.

---

### **Q5: What's the difference between in-place and not in-place solutions?**

**Answer:**

- **In-place:** Modify the array itself, no extra space O(1) - preferred
- **Not in-place:** Create new array/data structure, use O(n) space

Example: Reverse array in-place vs creating reversed copy.

---

### **Q6: How do you handle duplicates in an array?**

**Answer:** Depends on problem:

- **Remove duplicates:** Use two pointer or HashSet
- **Count duplicates:** Use HashMap or frequency array
- **Keep duplicates sorted:** Sort first, then identify clusters

---

### **Q7: When should you sort an array?**

**Answer:** Sort when:

- ✅ Problem needs elements in order (check if sorted helps)
- ✅ Sorting cost O(n log n) < original approach O(n²)
- ✅ Problem becomes easier after sorting (two pointer, etc)

Example: Two Sum - sorting costs O(n log n), then two pointer O(n) = O(n log n) total. Same as HashMap approach but uses O(1) space if returning indices isn't needed.

---

### **Q8: What's the time complexity of a nested loop on array?**

**Answer:**

```java
for (int i = 0; i < arr.length; i++) {
    for (int j = 0; j < arr.length; j++) {
        // operation
    }
}
// Outer loop: n times
// Inner loop: n times for each outer iteration
// Total: n * n = O(n²)
```

Avoid nested loops if possible. Use HashMap, sorting, or two pointer to optimize.

---

### **Q9: Can you modify an array while iterating?**

**Answer:** Not safely with enhanced for loop. Use:

```java
// Safe way - iterate backwards
for (int i = arr.length - 1; i >= 0; i--) {
    if (condition) arr[i] = newValue;  // OK
}

// Or collect indices first
List<Integer> toRemove = new ArrayList<>();
for (int i = 0; i < arr.length; i++) {
    if (condition) toRemove.add(i);
}
// Then remove in reverse order
for (int i = toRemove.size() - 1; i >= 0; i--) {
    // shift elements
}
```

---

### **Q10: How do you handle large arrays efficiently?**

**Answer:**

- Minimize extra space: prefer O(1) over O(n)
- Use in-place modifications when possible
- Avoid copying array unless necessary
- Choose right algorithm: O(n log n) sorting vs O(n) linear search
- Use primitive arrays for better performance than ArrayList


Arrays.sort() code

```
public static void quickSort(int[] arr) {
    if (arr.length == 0) return;
    quickSortHelper(arr, 0, arr.length - 1);
}

private static void quickSortHelper(int[] arr, int left, int right) {
    if (left < right) {
        int pivot = partition(arr, left, right);
        quickSortHelper(arr, left, pivot - 1);
        quickSortHelper(arr, pivot + 1, right);
    }
}

private static int partition(int[] arr, int left, int right) {
    int pivot = arr[right];  // Choose last element as pivot
    int i = left - 1;
    
    for (int j = left; j < right; j++) {
        if (arr[j] < pivot) {
            i++;
            // Swap
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    
    // Swap pivot to correct position
    int temp = arr[i + 1];
    arr[i + 1] = arr[right];
    arr[right] = temp;
    
    return i + 1;
}

// Usage
int[] arr = {50, 20, 30, 10, 40};
quickSort(arr);
System.out.println(Arrays.toString(arr));  // [10, 20, 30, 40, 50]
```


## Static Array (`int[]`) - Memory Layout

java

```java
int[] arr = new int[5];
```

**Memory structure:**
- Each `int` = **4 bytes**
- Array of 5 ints = **5 × 4 = 20 bytes** (contiguous block)
- Array reference itself = **8 bytes** (on 64-bit JVM)
- **Total heap memory = 28 bytes**

**Visual:**
```
arr → [Heap]
       |arr[0]|arr[1]|arr[2]|arr[3]|arr[4]|
       | 4B  | 4B  | 4B  | 4B  | 4B  |
       └─────────────────────────────────┘
       Contiguous memory block (20 bytes)
````

**Key:** Elements are **side-by-side in memory**, instant O(1) random access.