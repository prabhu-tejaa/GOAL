# Arrays - Subarrays, Subsequences & Subsets

## 1. Subarray

- Contiguous chunk of an array
- Must be **in order**, **no skipping**, **no reversing**
- Go **left to right only**

**Example:** `[1, 2, 3, 4, 5]`

All subarrays:

```
starting from 1:  [1]  [1,2]  [1,2,3]  [1,2,3,4]  [1,2,3,4,5]
starting from 2:  [2]  [2,3]  [2,3,4]  [2,3,4,5]
starting from 3:  [3]  [3,4]  [3,4,5]
starting from 4:  [4]  [4,5]
starting from 5:  [5]
```

Total = **15 subarrays**

❌ `[2, 1]` is NOT a subarray — going back  
❌ `[1, 3, 5]` is NOT a subarray — skipping elements

**number of subarrays = n × (n + 1) / 2**
where `n` = array size.
so for an array of size 9:
9 × 10 / 2 = **45 subarrays** 😵


---

## 2. Subsequence

- Can **skip** elements
- But still must go **left to right** (no reversing)

**Example:** `[1, 2, 3, 4, 5]`  
✅ `[1, 3, 5]` — skipped 2 and 4, but still left to right  
✅ `[2, 5]` — skipped 3 and 4, still left to right  
❌ `[5, 3, 1]` — reversed, NOT valid

---

## 3. Subset

- Any combination of elements
- **Order does NOT matter**
- Can skip anything

**Example:** `[1, 2, 3]`  
✅ `{1, 3}` — valid subset  
✅ `{3, 1}` — same subset, order doesn't matter  
✅ `{}` — empty set is a valid subset

---

## 4. Substring

- Same as subarray but for **Strings** instead of arrays
- Contiguous, in order, no skipping

**Example:** `"hello"`  
✅ `"ell"` — valid substring  
✅ `"hello"` — whole string is valid  
❌ `"hlo"` — skipping, NOT a substring

---

## Quick Comparison Table

|Type|Contiguous?|In Order?|Can Skip?|
|---|---|---|---|
|Subarray|✅ Yes|✅ Yes|❌ No|
|Subsequence|❌ No|✅ Yes|✅ Yes|
|Subset|❌ No|❌ No|✅ Yes|
|Substring|✅ Yes|✅ Yes|❌ No|

---

## Key Rule to Remember

> **Subarray = left to right, no skipping, no reversing, contiguous only.**