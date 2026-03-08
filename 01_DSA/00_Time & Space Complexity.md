## 1. The Efficiency Hierarchy

### **The Gold Standard (Fast & Efficient)**

- **O(1) - Constant Time:** The "instant" speed. No matter if you have 10 items or 10 million, the time taken stays the same.
    
    - _Example:_ Accessing an element in an array by its index.
        
- **O(logn) - Logarithmic Time:** Extremely efficient. As the data doubles, the time only increases by a tiny fraction.
    
    - _Example:_ Binary Search.
        

### **The Sweet Spot (Standard Performance)**

- **O(n) - Linear Time:** Fair and predictable. If you double the input size, the time taken doubles too.
    
    - _Example:_ Iterating through a simple list once.
        
- **O(nlogn) - Linearithmic Time:** The standard for good sorting algorithms. It’s slightly worse than linear but much better than quadratic.
    
    - _Example:_ Merge Sort or Quick Sort.
        

### **The Danger Zone (Slow & Heavy)**

- **O(n2) - Quadratic Time:** Performance starts to tank here. If the input is 10, it takes 100 steps. If the input is 100, it takes 10,000 steps.
    
    - _Example:_ Nested loops (like Bubble Sort).
        
- **O(2n) - Exponential Time:** This is where things get messy. Even small increases in input can make the program hang indefinitely.
    
    - _Example:_ Recursive Fibonacci.
        
- **O(n!) - Factorial Time:** The absolute "avoid at all costs" zone. Adding one more item makes the complexity explode.
    
    - _Example:_ Solving the Traveling Salesperson Problem via brute force.