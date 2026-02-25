# Java HashMap – DSA Quick Reference

HashMap() – Creates empty HashMap  
HashMap(int capacity) – Creates with initial capacity  
HashMap(int capacity, float loadFactor) – Creates with capacity + load factor  
HashMap(Map m) – Creates map from another map  

put(K key, V value) – Inserts or updates key-value pair  
putAll(Map m) – Inserts all entries from another map  
putIfAbsent(K key, V value) – Inserts only if key not present  

get(Object key) – Returns value for key (null if absent)  
getOrDefault(Object key, V defaultValue) – Returns value or default  

containsKey(Object key) – Checks if key exists  
containsValue(Object value) – Checks if value exists  

remove(Object key) – Removes entry by key  
remove(Object key, Object value) – Removes only if key maps to value  

replace(K key, V value) – Replaces value if key exists  
replace(K key, V oldValue, V newValue) – Replaces only if old value matches  

compute(K key, BiFunction fn) – Recomputes value for key  
computeIfAbsent(K key, Function fn) – Computes value if key absent  
computeIfPresent(K key, BiFunction fn) – Computes value if key present  

merge(K key, V value, BiFunction fn) – Merges value using function  

size() – Returns number of entries  
isEmpty() – Checks if map is empty  
clear() – Removes all entries  

keySet() – Returns set of all keys  
values() – Returns collection of all values  
entrySet() – Returns set of key-value pairs  

forEach(BiConsumer action) – Iterates over entries  

Default capacity – 16  
Default load factor – 0.75  

Average time complexity – O(1)  
Worst-case time complexity – O(n)  