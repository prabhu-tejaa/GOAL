WHEN to Use HashMap (Decision Making)
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
 "I'd use a HashMap to store `[key → value]` pairs because I need O(1) lookup. For every element, I can check if its complement exists in the map in constant time."
