https://www.goldmansachs.com/careers/discover/virtual-interview-prep.pdf

### Phase 1: The Filters (Rounds 1–2)

These rounds are designed to cut the high volume of applicants.

- **Round 1: Online Assessment (HackerRank)**
    
    - **Duration:** ~120 minutes.
        
    - **What is asked:** * **2 Coding Questions:** One LC-Medium (Arrays/Strings) and one LC-Hard (DP or Graphs).
        
        - **Math/Aptitude:** Probability, combinatorics, and logical reasoning (GS loves math).
            
        - **CS Fundamentals:** MCQs on OS, DBMS, and Linux commands.
            
- **Round 2: Technical Screen (CoderPad)**
    
    - **Duration:** 45–60 minutes.
        
    - **What is asked:** You will live-code in an editor where the interviewer can **run** your code.
        
    - **Common Questions:** "Highest Average Student Score" (High Five), "First non-repeating character," or "Kill Process Tree."
        
    - **The Catch:** They will grill you on **Time & Space complexity** ($O(N)$ vs $O(\log N)$) before you even finish typing.
        

---

### Phase 2: The "Superday" (Rounds 3–6)

If you pass the filters, you have 3–4 back-to-back interviews in one day.

- **Round 3: Advanced DSA & Problem Solving**
    
    - **Focus:** Complex logic.
        
    - **Questions:** Sliding Window (e.g., "Smallest subarray with sum K"), Graph traversal (BFS/DFS), or "Trapping Rain Water."
        
- **Round 4: System Design (HLD & LLD)**
    
    - **Focus:** This is the "Associate" bar.
        
    - **LLD (Low-Level Design):** Design a **Parking Lot** or a **Elevator System** using OOPS principles (Classes, Interfaces).
        
    - **HLD (High-Level Design):** Design a **Real-time Trade Processing System** or a **Distributed Cache**. You must mention the **Saga Pattern** for transactions.
        
- **Round 5: Java & Engineering Practices**
    
    - **Focus:** Deep technical depth.
        
    - **Questions:** G1 Garbage Collector, `ConcurrentHashMap` internals, and **Multithreading** (locks, race conditions).
        
    - **The "Pro" Touch:** They may ask about Git branching strategies or CI/CD pipelines.
        
- **Round 6: Behavioral / Hiring Manager**
    
    - **Focus:** Culture fit and "The Goldman Way."
        
    - **Questions:** "Tell me about a time you failed," "How do you handle a conflict with a senior?"
        
    - **The Secret:** Use the **STAR method** and align your answers with their **14 Business Principles**.

https://leetcode.com/discuss/interview-question/334671/goldman-sacks-july-2019-hackerrank-2
https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/

# Round 5: Java & Engineering Practices
https://www.geeksforgeeks.org/interview-experiences/goldman-sachs-interview-experience-for-java-developer-3-years-experienced/
https://github.com/a11exe/java-interview/blob/main/questions/concurrency.md
### 1. Core Java & Internals (The "How it Works" Layer)

- **HashMap & HashSet Internals:**
    
    - **Buckets & Hashing:** How the index is calculated (`hash & (n-1)`).
        
    - **Collision Handling:** Linked List vs. **Red-Black Tree** (know the threshold of 8).
        
    - **Load Factor:** Why 0.75? (The trade-off between space and time).
        
- **JVM Memory Management:**
    
    - **Heap vs. Stack:** What is thread-local (Stack) vs. shared (Heap).
        
    - **Metaspace:** Where class metadata is stored (replaced PermGen).
        
    - **Garbage Collection:** Deep dive into **G1GC** (Regions, Humongous Objects) and **ZGC** (for ultra-low latency).
        
- **String Mastery:** Why is `String` immutable? (Security, Caching, and Synchronization). Understand `String Pool`.
    

---

### 2. Concurrency & Multithreading (The "High-Performance" Layer)

Goldman is a bank; their systems handle thousands of transactions per second. This is usually the hardest part of the interview.

- **The Java Memory Model (JMM):**
    
    - **`volatile` keyword:** "Happens-before" relationship and visibility.
        
    - **Atomic Classes:** How `AtomicInteger` uses **CAS (Compare-And-Swap)** instead of locking.
        
- **Locks:**
    
    - `synchronized` vs. `ReentrantLock` (fairness, `tryLock`, and interruptible locks).
        
    - **Deadlocks:** How to detect, prevent, and resolve them.
        
- **Executor Framework:**
    
    - `FixedThreadPool` vs. `CachedThreadPool`.
        
    - **`CompletableFuture`:** How to chain asynchronous tasks (crucial for modern microservices).
        
- **Virtual Threads (Java 21):** Why they are "lightweight" and how they differ from platform threads.
    

---

### 3. Modern Java (Java 8 to Java 25+)

- **Lambdas & Streams:** Mastering `map`, `filter`, `reduce`, and `flatMap`.
    
- **Functional Interfaces:** `Predicate`, `Function`, `Consumer`, and `Supplier`.
    
- **Optional:** How to avoid `NullPointerException`.
    
- **Records & Sealed Classes:** Using these for cleaner, immutable domain models.
    

---

### 4. Engineering Practices (The "Pro" Layer)

This is what sets an L2 apart from a junior. You are expected to know how to "ship" code.

- **Design Patterns:**
    
    - **Singleton:** Implement a thread-safe version using **Double-Checked Locking**.
        
    - **Strategy & Factory:** Used for different payment methods or asset classes.
        
    - **Observer:** How stock price tickers update the UI.
        
- **Testing Rigor:**
    
    - **Unit Testing:** Using **JUnit 5** and **Mockito**.
        
    - **Integration Testing:** How to test with a real database using **Testcontainers**.
        
- **CI/CD & Git:**
    
    - **Branching:** GitFlow vs. Trunk-based development.
        
    - **Pipelines:** Stages like Build -> Scan (SonarQube) -> Test -> Deploy.
        
- **Solid Principles:** Be able to explain "Dependency Inversion" or "Interface Segregation" with a real-world example.

# DSA

**Edge Cases:** For every problem, explicitly mention how you handle:

- Empty strings/arrays
    
- `null` inputs
    
- Integer overflow (use `long` in Java if necessary)
    
- Negative numbers
file:///C:/Users/91951/AppData/Local/Temp/Goldman%20Sachs%20Tagged%20LeetCode%20Problems%20.pdf
https://github.com/snehasishroy/leetcode-companywise-interview-questions/tree/master/goldman-sachs

https://leetcode.com/problems/trapping-rain-water
