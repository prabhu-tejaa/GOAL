09-03-2026 - 21:00
## **Hashing**
Hashing is a **technique** that converts any input into a fixed number (hash code).
```
Input: "Alice"  →  [Hash Function]  →  Output: 5 (a number)
Input: 101      →  [Hash Function]  →  Output: 1 (a number)
Input: "Bob"    →  [Hash Function]  →  Output: 3 (a number)
```
**Purpose:** Convert large data into a small number (bucket index).

## **HASHMAP = Data Structure**

HashMap is a **data structure** that stores data in **key-value pairs**. It USES hashing internally. 
**HashMap:** Scattered memory.

```
HashMap uses hashing to:
- Take your key
- Hash it → get a number
- Use that number as array index
- Store your key-value pair there
```

### The Structure

A `HashMap` is essentially an **Array**, but each "slot" in that array isn't just a single value it's the start of a **Linked List**.

- **The Array (The Buckets):** This is the main structure. It has indices (0, 1, 2, 3...).
    
- **The Node (The Entry):** Each item you "put" into the map is wrapped in a `Node` object that contains:
    
    1. The **Key**
        
    2. The **Value**
        
    3. The **Hash**
        
    4. A **Pointer (`next`)** to the next Node (this is the Linked List part).

```
Array Index 1:
┌─────────────────────────────┐
│  Entry / Node               │
├─────────────────────────────┤
│  key      │ 101             │
│  value    │ "Alice"         │
│  hash     │ 1 (bucket index)│
│  next     │ → (null)     │
└─────────────────────────────┘
```

In Java’s `HashMap`, the default initial length (capacity) of the array is **16**.

Why 16? (The Power of 2)
The length is always a **power of 2** (2n). It starts at 16 (2^4), and every time it grows, it doubles (32,64,128…).

Example:
```
HashMap<Integer, Integer> map = new HashMap<>();
map.put(101, "Alice");
```

HashMap methods:

- **put(K key, V value)**: Adds a key-value pair. If the key exists, it updates the value.

- **get(Object key)**: Returns the value for a key, or `null` if the key is not found.

- **containsKey(Object key)**: Returns `true` if the key exists. Essential for checking "seen" elements.

- **getOrDefault(K key, V defaultValue)**: Returns the value for the key, or the `defaultValue` if the key is missing. (Best for counting frequencies).

- **putIfAbsent(K key, V value)**: Adds the pair only if the key is not already present.

- **computeIfAbsent(K key, Function)**: If the key is missing, it computes a value (like `new ArrayList()`) and adds it. (Best for Group Anagrams or Adjacency Lists).

- **remove(Object key)**: Removes the key-value pair for the specified key.

- **size()**: Returns the number of key-value pairs currently in the map.

- **isEmpty()**: Returns `true` if the map contains no key-value pairs.

- **keySet()**: Returns a `Set` of all keys. Use this to iterate through keys only.

- **values()**: Returns a `Collection` of all values.

- **entrySet()**: Returns a `Set` of `Map.Entry<K, V>`. The most efficient way to loop when you need both Key and Value.

- **clear()**: Removes all key-value pairs from the map.

### **Hash Collisions**
What happens when two keys hash to the same index?
**Java's Solution: Chaining**
Instead of a single value, each bucket stores a **linked list** (or tree in Java 8+) of entries:

```
Array Index 1:
┌─────────────────────────────┐      ┌─────────────────────────────┐
│  Entry (Node 1)             │      │  Entry (Node 2)             │
├─────────────────────────────┤      ├─────────────────────────────┤
│  key      │ 101             │      │  key      │ 17              │
│  value    │ "Alice"         │      │  value    │ "seventeen"     │
│  hash     │ 1               │      │  hash     │ 1               │
│  next     │ ──────────────→ │──────→  next     │ null            │
└─────────────────────────────┘      └─────────────────────────────┘
           ↑
      First node
     (head of list)
```

Example:

```
HashMap<Integer, String> map = new HashMap<>();
map.put(101, "Alice");      // hash(101) → index 1
map.get(101);               // hash(101) → index 1 → O(1)
HashMap<Integer, String> map = new HashMap<>();
map.put(1, "one");
map.put(17, "seventeen");

// If array length = 16:
// hash(1) = 1 % 16 = 1
// hash(17) = 17 % 16 = 1  ← COLLISION! Same index
```

Normally, collisions are handled by a **LinkedList**. But if many keys land in the _same_ bucket, searching that list becomes slow O(n).

To fix this, Java 8 introduced **Treeification**:

- **The Threshold:** When a single bucket's LinkedList reaches **8 nodes**, and the total array capacity is at least **64** and its the array capacity is **<64** then the map will **Resize**
    
- **The Change:** The LinkedList is converted into a **Red-Black Tree** (a balanced binary search tree).
    
- **The Benefit:** Searching a list takes O(n), but searching a balanced tree takes O(logn). It prevents a "Hash Collision Attack" from slowing down your app.

### **Load Factor**
It is a measure of how full the `HashMap` is allowed to get before its capacity is automatically increased.

- **Default Value:** `0.75` (75%).
- **Why 0.75?** It’s a trade-off. A higher value (like 0.9) saves memory but increases collisions. A lower value (like 0.5) reduces collisions but wastes memory.

### **Resizing**:
When you reach that 75% limit, you don't just add one more slot. You **double** the size of the lot to **32 slots**.
It happens when `Size > (Capacity * Load Factor)`.

- For a default map: `Size > (16 * 0.75)`. Once you add the **13th element**, it resizes.
### What happens during Resize? (O(n))

1. **New Array:** A new internal array is created with **double** the capacity (e.g., from 16 to 32).
2. **Rehashing:** Every single existing element is "re-calculated" because the formula `(capacity - 1) & hash` changes when capacity changes.
3. **Transfer:** All elements are moved to their new positions in the larger array.

### **Time complexity:**
- Best case (no collisions): O(1)
- Worst case (all collisions): O(n) if all keys hash to same index
- Average case (good hash function): O(1)

**_"What is the worst case time complexity of a HashMap search?"_**
- **Before Java 8:** O(n) (because of long LinkedLists).
- **After Java 8:** O(logn) (because long lists become Trees).
	


### **WHEN to Use HashMap (Decision Making))**
	Use HashMap when:
	✅ Need O(1) lookup → HashMap.containsKey(), HashMap.get()
	✅ Need to store key-value pairs → cache, frequency, index mapping
	✅ Need to count occurrences → word frequency, character count
	✅ Need to find complements → Two Sum, valid anagram check
	
	Don't use HashMap when:
	❌ Need ordered iteration → use TreeMap
	❌ Need thread-safety → use ConcurrentHashMap
	❌ Need to track insertion order → use LinkedHashMap
	❌ Just checking existence → HashSet is lighter

**Interview answer template:**

> "I'd use a HashMap to store `[key → value]` pairs because I need O(1) lookup. For every element, I can check if its complement exists in the map in constant time."

### **2. Time & Space Complexity (They ALWAYS ask)**

**Interview will probe:**
- "What's the time complexity?"
- "Why is it O(n)?"
- "What about space?"
- "What's the worst case?"

	HashMap<Integer, Integer> map = new HashMap<>();
	
	map.put(key, value);      // O(1) average, O(n) worst
	map.get(key);             // O(1) average, O(n) worst
	map.containsKey(key);     // O(1) average, O(n) worst
	map.remove(key);          // O(1) average, O(n) worst
	map.keySet();             // O(n) to iterate
	map.values();             // O(n) to iterate
	map.entrySet();           // O(n) to iterate
	
	Space: O(n) where n = number of entries

**Interview answer:**

> "Time complexity is O(n) because we iterate through the array once, and each HashMap operation (put, get) is O(1) average. Space complexity is O(n) because we store up to n key-value pairs."

**Follow-up they might ask:**

> "Why O(1) average and not always?"

**Your answer:**

> "HashMap uses a hash function to map keys to array indices. If there are no collisions, we get O(1) lookup. But in the worst case, if all keys hash to the same index (poor hash function or unlucky input), we'd have O(n) because we'd need to traverse a linked list of n collisions. However, Java's HashMap automatically resizes when load factor exceeds 0.75, which keeps collisions low on average."

### Key DSA Concepts (Theory)
- **hashCode()**: Method used to determine the bucket index for a key.
- **equals()**: Method used to distinguish between keys within the same bucket (collision handling).
- **Collision**: When two different keys map to the same bucket index.
- **Load Factor**: The threshold (default 0.75) that determines when the map capacity should double (Rehashing).

### **Null Keys/Values**

```java
// WORKS in HashMap (unique feature)
map.put(null, "value");     // ✅ HashMap allows null key
map.put("key", null);       // ✅ HashMap allows null values
map.get(null);              // ✅ Returns "value"
```

**Interview answer:**

> "HashMap is the only standard map in Java that allows null keys and null values. If you try this with Hashtable or ConcurrentHashMap, you'll get a NullPointerException."


Interviewer: "Why O(n)? What about worst case?" 

You: "HashMap operations (get, put, containsKey) are O(1) on average because the hash function distributes keys evenly. Worst case is O(n) if all keys hash to the same bucket, but Java's HashMap resizes automatically to keep load factor below 0.75, so worst case is rare in practice."

# **HashSet**

## **What is HashSet?**

HashSet is a **data structure** that stores **only values** (no key-value pairs). It uses **hashing internally** (like HashMap) but doesn't store keys.

**Purpose:** Check if something exists in a set, store unique values.

```
HashMap:  {101 → "Alice", 17 → "seventeen"}  (key-value pairs)
HashSet:  {101, 17, 42}                      (just values)
```

## **Internal Structure**

HashSet internally uses a HashMap!

```
// Behind the scenes, HashSet uses HashMap private transient 
HashMap<E,Object> map; 
// When you add to HashSet: 
hashSet.add(101); 
// Actually does: map.put(101, PRESENT); 
```

So HashSet is basically: 
- **Array of buckets** (like HashMap) 
- Each bucket has a **linked list** (or tree) 
- But stores **only the value, not a key-value pair** 
## **How it Works** 
### **add(value)**  
hashSet.add(101);
1. Hash the value: hash(101) = 1 
2. Go to index 1 in array 
3. Add 101 to the linked list at that bucket 
4. Time: O(1) average 
### **contains(value)**  
hashSet.contains(101);
1. Hash the value: hash(101) = 1 
2. Go to index 1 in array 
3. Search linked list for 101 
4. Return true/false 
5. Time: O(1) average 
### **remove(value)** 
hashSet.remove(101);
1. Hash the value: hash(101) = 1 
2. Go to index 1 in array 
3. Remove 101 from linked list 
4. Time: O(1) average

## **Time Complexity**

|Operation|Time|Space|
|---|---|---|
|**add(value)**|O(1) avg, O(n) worst|O(1)|
|**contains(value)**|O(1) avg, O(n) worst|O(1)|
|**remove(value)**|O(1) avg, O(n) worst|O(1)|
|**Iterate all**|O(n)|-|

**Space Complexity:** O(n) where n = number of elements

## **HashSet Methods**

```
HashSet<Integer> set = new HashSet<>(); 
set.add(101); // Add element 
set.contains(101); // Check if exists: true/false 
set.remove(101); // Remove element 
set.size(); // Number of elements 
set.isEmpty(); // Is empty? 
set.clear(); // Remove all 
set.iterator(); // Iterate through elements
```

Example:
```
HashSet<Integer> seen = new HashSet<>(); 
for (int num : nums) { 
	if (seen.contains(num)) { 
		return true; // Duplicate found 
		} 
	seen.add(num); 
} 
return false;
```

**Why HashSet?** We only care about existence, not storing indices. HashSet is lighter than HashMap.

# **TreeMap**

TreeMap is a **data structure** that stores **key-value pairs** (like HashMap) but **keeps them sorted by key**. 
**Purpose:** Store key-value pairs in sorted order.

```
HashMap: {17→"seventeen", 101→"Alice"} (random order) 
TreeMap: {1→"one", 17→"seventeen", 101→"Alice"} (sorted by key)
```

## **Internal Structure**

TreeMap uses a **Red-Black Tree** (balanced binary search tree), NOT an array.

![[Pasted image 20260308222231.png]]

**Why Red-Black Tree?** 
- Keeps keys sorted 
- Balanced (doesn't get too tall on one side) 
- O(log n) operations

## **How it Works** 
### **put(key, value)**

```
treeMap.put(17, "seventeen"); 
1. Find correct position in tree (maintaining sorted order) 
2. Insert the key-value pair 
3. Rebalance if needed 
4. Time: O(log n)
```

### **get(key)**

```
treeMap.get(17);
1. Search tree for key 17 
2. Return value if found 
3. Time: O(log n)
```

## **Time Complexity**

|Operation|Time|Space|
|---|---|---|
|**put(K, V)**|O(log n)|O(1)|
|**get(K)**|O(log n)|O(1)|
|**containsKey(K)**|O(log n)|O(1)|
|**remove(K)**|O(log n)|O(1)|
|**Iterate (sorted)**|O(n)|-|

**Space Complexity:** O(n) where n = number of elements

### TreeMap Methods

```
TreeMap<Integer, String> treeMap = new TreeMap<>();

treeMap.put(17, "seventeen");      // Add pair
treeMap.get(17);                   // Get value: O(log n)
treeMap.containsKey(17);           // Check if key exists: O(log n)
treeMap.remove(17);                // Remove: O(log n)
treeMap.firstKey();                // Smallest key
treeMap.lastKey();                 // Largest key
treeMap.headMap(100);              // All keys < 100
treeMap.tailMap(50);               // All keys >= 50
treeMap.keySet();                  // All keys in sorted order
```

```
Do you need KEY → VALUE mapping? 
│ 
├─ YES: Do you need sorted order? 
│ 	├─ YES → TreeMap (O(log n) but sorted) 
│ 	└─ NO → HashMap (O(1), fastest) 
└─ NO: Just checking if value exists? 
	└─ HashSet (lighter, O(1))
```

# **HashMap vs HashSet vs TreeMap**

|Feature|HashMap|HashSet|TreeMap|
|---|---|---|---|
|**Stores**|Key-value pairs|Only values|Key-value pairs|
|**Internal Structure**|Array + linked lists|Array + linked lists|Red-Black tree|
|**put/add(K,V)**|O(1) avg|O(1) avg|O(log n)|
|**get(K)**|O(1) avg|O(1) avg|O(log n)|
|**contains(K)**|O(1) avg|O(1) avg|O(log n)|
|**remove(K)**|O(1) avg|O(1) avg|O(log n)|
|**Sorted?**|❌ No|❌ No|✅ Yes|
|**Iteration Order**|Random|Random|Sorted by key|
|**Null Support**|1 null key|1 null value|No nulls|
|**Use When**|Key→value mapping|Just existence check|Need sorted order|

# Additional learnings

## What is "hash lookup overhead"?

When you do `map.put('a', 1)` or `map.get('a')`:

```
HashMap steps:
1. Convert 'a' to a hash code (function call) ← cost
2. Find bucket based on hash (computation) ← cost
3. Handle collisions if needed (extra checks) ← cost
4. Return value

Array steps:
1. Do math: 'a' - 'a' = 0
2. Access freq[0] directly ← instant
```

**"Overhead" = extra work HashMap does behind the scenes.**
Array is faster because it's just **one direct math calculation + array access**.