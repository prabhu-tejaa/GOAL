## Binary Search

Binary search is a highly efficient algorithm for finding an item from a **sorted** list of items. It works by repeatedly dividing in half the portion of the list that could contain the item until you've narrowed down the possible locations to just one.

## How It Works

To use binary search, the data **must be sorted**. Here is the logic:

1. **Find the Middle:** Look at the element in the exact middle of your list.
    
2. **Compare:** If the middle element is your target, **you're done!**
    
    - If the target is **smaller** than the middle element, repeat the search on the **left half**.
        
    - If the target is **larger** than the middle element, repeat the search on the **right half**.
        
3. **Repeat:** Keep halving the search area until the item is found or the list is empty

Complexity of binary search is **O(logn)**.

**Binary Search (O(logn)):** For 1,000,000 items, it will take **no more than 20 steps**.

This is the core formula of binary search to find the mid = left + (right - left) / 2

Here, **BODMAS** is the grammar that ensures the Machine understands the Logic
1. Brackets
2. Orders (x^ or roots)
3. Division
4. Multiplication
5. Addition
6. Subtraction

## row = mid / n 
## col = mid % n

**Math:** 11/4=2 (In programming, we ignore the decimals/remainders here).
- **Scenario:** You have **11 eggs**. Each carton holds **4**.
- **Math:** 11(mod4)=3.

In computers or coding in leetodde 9/3 = 4 and 9/2 = 8;


# **Search Space Reduction**

