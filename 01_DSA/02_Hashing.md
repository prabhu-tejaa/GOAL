

### **1. WHEN to Use HashMap (Decision Making))**
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

### HashMap: Essential Java Methods for DSA

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