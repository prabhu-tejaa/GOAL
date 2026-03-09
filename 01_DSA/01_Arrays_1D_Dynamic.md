## Core Concept

- **Static Array**: Fixed size at creation (`int[] arr = new int[5]`)
- **Dynamic Array**: Resizable, grows/shrinks as needed (ArrayList in Java)

---

## Java ArrayList Basics

### Declaration & Initialization

```java
ArrayList<Integer> list = new ArrayList<>();
ArrayList<String> names = new ArrayList<>(10); // initial capacity 10
```

### Core Operations

|Operation|Code|Time|Space|
|---|---|---|---|
|Add (end)|`list.add(5)`|O(1) amortized|O(1)|
|Add (position)|`list.add(2, 5)`|O(n)|O(1)|
|Get|`list.get(0)`|O(1)|—|
|Remove|`list.remove(0)`|O(n)|O(1)|
|Set|`list.set(0, 5)`|O(1)|—|
|Size|`list.size()`|O(1)|—|
|Contains|`list.contains(5)`|O(n)|—|

### Common Methods

```java
list.add(element);           // append
list.add(index, element);    // insert at position
list.get(index);             // access element
list.remove(index);          // delete by index
list.remove(Integer.valueOf(5)); // delete by value
list.size();                 // length
list.isEmpty();              // check empty
list.clear();                // remove all
list.contains(element);      // check existence
list.indexOf(element);       // find index
```

---

## Why Dynamic Arrays?

### Problems That Need Them

1. **Unknown input size** → Build result as you go
2. **Accumulating results** → Graph adjacency lists, subsets, permutations
3. **Flexible resizing** → Add/remove during iteration
4. **Avoiding null checks** → Pre-sized arrays need careful boundary handling

### Example: When to Use

```java
// ❌ Don't know result size upfront
int[] result = new int[???]; // How big?

// ✓ Use ArrayList
ArrayList<Integer> result = new ArrayList<>();
for (...) {
    result.add(computed_value);
}
```

---

## Resizing Mechanics (Behind the Scenes)

When ArrayList reaches capacity:

1. Allocates **new array** (usually 1.5x or 2x size)
2. **Copies all elements** from old array
3. **Deallocates** old array

**Cost:** O(n) for one add operation when resize happens, but **amortized O(1)** across many additions.

---

## Common DSA Patterns

### Pattern 1: Collecting Results

```java
ArrayList<Integer> result = new ArrayList<>();
for (int num : nums) {
    if (condition) {
        result.add(num);
    }
}
return result.stream().mapToInt(Integer::intValue).toArray();
```

### Pattern 2: Two Pointers with Dynamic Storage

```java
ArrayList<Integer> list = new ArrayList<>();
int left = 0, right = nums.length - 1;
while (left < right) {
    if (condition) {
        list.add(nums[left]);
    }
    left++;
}
```

### Pattern 3: Graph/Tree Adjacency List

```java
ArrayList<ArrayList<Integer>> graph = new ArrayList<>();
for (int i = 0; i < n; i++) {
    graph.add(new ArrayList<>()); // each node has dynamic neighbor list
}
graph.get(0).add(1); // node 0 connects to node 1
```

### Pattern 4: Nested ArrayList for 2D Data

```java
ArrayList<ArrayList<Integer>> matrix = new ArrayList<>();
for (int i = 0; i < rows; i++) {
    matrix.add(new ArrayList<>()); // each row is dynamic
}
```

---

## ArrayList vs Array: When to Choose

|Scenario|Use ArrayList|Use Array|
|---|---|---|
|Size unknown upfront|✓|❌|
|Size fixed & known|❌|✓|
|Need frequent insertion/deletion|✓|❌|
|Performance-critical inner loop|❌|✓|
|Random access heavy|✓|✓ (same speed)|
|Memory sensitive|❌|✓|

---

## Interview Red Flags & Tips

### ✓ Do This

- Use ArrayList when size is unknown
- Convert to array for final return if needed
- Know the time complexity implications

### ❌ Avoid This

- Creating ArrayList of ArrayList unnecessarily (use 2D array if size known)
- Removing from middle of ArrayList in loop (causes O(n²) bugs)
- Forgetting to convert ArrayList back to array for return type

---

## Quick Complexity Reference

```
ArrayList Operation | Time | Notes
add()              | O(1) amortized | O(n) when resize happens
get()              | O(1) | direct index access
remove(index)      | O(n) | elements shift
remove(value)      | O(n) | search + shift
contains()         | O(n) | linear search
size()             | O(1) | tracks capacity
```

## Dynamic Array (ArrayList) - Memory Layout

java

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(5);
list.add(10);
```

**What happens behind the scenes:**

1. **ArrayList object** (on heap):
   - Stores reference to internal array
   - Stores `size` (current elements)
   - Stores `capacity` (allocated space)
   - **Size: ~24-32 bytes** (depends on JVM)

2. **Internal backing array** (on heap):
   - Initially: capacity = 10 (default)
   - Each element = **reference to Integer object** = **8 bytes** (on 64-bit JVM)
   - Array of 10 refs = **80 bytes**

3. **Integer objects themselves** (on heap):
   - Each `Integer` wrapper = **16 bytes** (object header + int value)
   - Two Integer objects = **32 bytes**

**Visual:**
```java
list → [ArrayList Object (heap)]
       ├─ size: 2
       ├─ capacity: 10
       └─ elementData → [Backing Array (heap)]
                        |ref|ref|ref|...|
                        | 8B | 8B | 8B |... (10 slots)
                        └────────────────┘
                          Points to:
                        [Integer(5)] [Integer(10)]
                         16 bytes     16 bytes
```

![[Pasted image 20260309140320.png]]

## When ArrayList Resizes

java

```java
ArrayList<Integer> list = new ArrayList<>(); // capacity = 10
list.add(1);  // size = 1, capacity = 10 ✓
list.add(2);  // size = 2, capacity = 10 ✓
// ... 10 additions ...
list.add(11); // RESIZE TRIGGERED!
```

**Resize process:**

1. Create **new backing array** (capacity = 10 × 1.5 = 15)
2. **Copy all references** from old array to new (O(n) operation)
3. **Old array garbage collected**
4. Add new element to new array

**Memory at that moment:**

- Old backing array: **80 bytes** (waiting for GC)
- New backing array: **120 bytes** (15 slots × 8 bytes)
- **Temporary spike in memory usage**

---

## Why This Matters for Interviews

**Question: "What's the space complexity of ArrayList operations?"**

- `add()` at end: **O(1) amortized** (spreads resize cost over many adds)
- `add(index)` in middle: **O(n)** (must shift all elements)
- Getting element: **O(1)** direct access via reference

**Question:**Why use int[] over ArrayList< Integer >?"

- Performance: int[] is 6× more memory efficient per element
- Cache locality: Contiguous memory = better CPU cache hits
- GC pressure: No wrapper object allocation

## Quick Memory Estimates

java

```java
// Static array
int[] arr = new int[1000];
// ≈ 4000 bytes (1000 × 4) + 8 bytes (ref) = 4,008 bytes

// Dynamic array
ArrayList<Integer> list = new ArrayList<>();
// Empty: ≈ 32 bytes (ArrayList object) + 80 bytes (backing array) = 112 bytes
// After 1000 adds: ≈ 32 + (2000 refs × 8) + (1000 Integer objects × 16) ≈ 24,032 bytes
```

**int[] wins on memory.** ArrayList wins on flexibility.

## All Data Types - Size Chart

| Type      | Primitive Size | Wrapper Size    | Reference Size |
| --------- | -------------- | --------------- | -------------- |
| `int`     | 4 bytes        | Integer = 16B   | 8 bytes        |
| `long`    | 8 bytes        | Long = 24B      | 8 bytes        |
| `double`  | 8 bytes        | Double = 24B    | 8 bytes        |
| `boolean` | 1 byte         | Boolean = 17B   | 8 bytes        |
| `char`    | 2 bytes        | Character = 18B | 8 bytes        |

# Additional learnings

## When Array is Faster than HashMap

**Only when:**

1. **Fixed, small range of values** (like 26 letters)
2. **Simple conversion to index** (like `c - 'a'`)

**Why faster:**

- Array: one math operation + direct memory access = O(1) with **low constant**
- HashMap: hash function + bucket lookup + collision handling = O(1) with **high constant**

Both are O(1), but array has **less overhead**.

---

## When HashMap is Better

1. **Unknown or large range** (Unicode, arbitrary integers, strings as keys)
2. **Sparse data** (only 5 unique chars, but potential 26) — HashMap uses only space needed
3. **Flexibility** (works with any type of data)

---

## Valid Anagram Case

**Array wins** because:

- Fixed range (26 letters only)
- Simple index calculation
- No collisions, no hashing overhead

**If problem allowed Unicode:** HashMap would win because you can't map arbitrary Unicode to fixed array.

---

## In Interviews—When to Say What

**"I'll use frequency array because the constraint is lowercase English only — direct array access is faster than HashMap."**

vs.

**"I'll use HashMap because it handles any characters and uses only space for unique chars."**

Both are correct. Choose based on **constraints**.

Clear?