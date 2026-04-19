Let me fetch the phone screening and interview loop pages directly from Amazon.Here's the full breakdown of all 3 phases, in detail:

---

## 🟡 Phase 1: Online Assessment (OA)

**Time: ~2.5 hours total | Comes first, any day now**

---

### 1️⃣ Coding Assessment (~70 mins)

2 DSA problems on HackerRank.

Common topics: Arrays, Strings, HashMaps, Linked Lists, Two Pointers, Sliding Window, BFS/DFS.

Tips:

- You CAN use Google for docs (Java/Python official docs etc.)
- Browser usage is logged — don't open sketchy sites
- No copy-pasting, no print screen
- If stuck on one problem, move to the next

---

### 2️⃣ Workstyles Assessment (~15 mins)

Multiple choice situational questions tied to Leadership Principles.

Example questions:

- "Your teammate disagrees with your solution — what do you do?"
- "You realise you made an error in code already shipped — what's your first step?"

Just pick the most responsible, ownership-driven answer. No overthinking needed.

---

### 3️⃣ Work Sample Simulation (~60 mins)

Amazon puts you in realistic SDE work scenarios.

You might see things like:

- An email thread where teammates are debating a technical decision — pick the best response
- A situation where a customer is affected by a bug — what do you prioritise?
- Choosing between two design approaches with trade-offs

Think: **"What would a responsible Amazon engineer do?"** — always lean towards customer impact and ownership.

---

### 4️⃣ Feedback Survey (~5 mins)

Mandatory. Don't skip it — failure to complete the survey will delay your results.

---

## 🟠 Phase 2: Phone Screening

**Time: ~60 mins | Comes 1–2 weeks after OA**

They call it phone screening but it's really a DSA + behavioural round. It's an **elimination round** — so take it seriously.

---

### Part A — Behavioural (~20 mins)

Phone screening begins with 2 behavioural questions, often around a specific Leadership Principle like Customer Obsession.

Example questions:

- "Tell me about a time you went above and beyond for someone"
- "Tell me about a project you're proud of and your role in it"
- "Tell me about a time you disagreed with a teammate"

Use **STAR format** — Situation → Task → Action → Result. Include numbers/metrics where possible.

---

### Part B — Coding (~40 mins)

One medium-level LeetCode problem, solved on Livecode (Amazon's real-time coding platform) while the interviewer watches.

Topics likely to appear:

- Stacks, Queues
- String manipulation
- Arrays / HashMaps
- Binary Search

Talk through your thinking out loud. Explain before you code. Mention edge cases.

---

## 🔴 Phase 3: Interview Loop

**Time: 3–4 rounds, each ~55–60 mins | Final stage**

Based on candidate reports, the general structure is: Rounds 1 & 2 are DSA coding rounds (one problem each), Round 3 is System Design, and Round 4 is a behavioural deep-dive — though some candidates only get 3 rounds.

Every round has 45 mins of technical questions + 15 mins of Leadership Principles (2 LPs per round).

---

### 🔵 Rounds 1 & 2 — DSA Coding

One problem per round on Livecode. They evaluate:

- Correct, working, syntactically valid code (no pseudo code)
- Edge case handling
- Time & space complexity — they ask proper 5–10 mins and cross-question a lot on how you can improve.
- Clean code structure

Topics:

- Linked Lists (reverse, detect cycle)
- Trees (LCA, level order, height)
- Graphs (BFS, DFS)
- Dynamic Programming
- Binary Search

---

### 🔵 Round 3 — System Design (Light for SDE I)

For SDE I, scope is basic — no distributed systems expected.

Example problems:

- Design a Parking Lot system
- Design a Library/Bookstore system
- Design a URL Shortener

What they look for:

- Define classes, objects, methods
- Basic database tables
- Handle edge cases ("what if parking lot is full?")

---

### 🔵 Round 4 — Behavioural Deep Dive + Bar Raiser

This is the Bar Raiser round — an additional technical/behavioural evaluation by a senior engineer.

LPs are taken very seriously — people get rejected purely on LP answers. Questions aren't asked directly — you're given a statement and have to figure out which LP applies.

Key LPs for SDE I to prepare:

|Leadership Principle|Example Question|
|---|---|
|Customer Obsession|"Tell me about a time you prioritised the user over everything else"|
|Ownership|"Tell me about a time you fixed something that wasn't your responsibility"|
|Invent & Simplify|"Tell me about a time you found a simpler solution to a complex problem"|
|Dive Deep|"Tell me about a time you used data to solve a problem"|
|Deliver Results|"Tell me about a time you met a really tough deadline"|
|Learn & Be Curious|"Tell me about something you taught yourself recently"|

Prepare **one strong STAR story per LP** with real numbers — "improved performance by 40%", "finished 1 week early", etc.

---

## ⏱️ Your Full Prep Timeline

|When|What|
|---|---|
|**Right now → Week 2**|OA prep — LeetCode easy/mediums + Amazon's free practice test|
|**Week 2–3**|Phone screen prep — 2–3 STAR stories + 1 coding problem daily|
|**Week 3–6**|Loop prep — more LeetCode mediums + LP stories + basic system design|

	**Start today with:** [hr.gs/TheAmazonCodingDemo](https://hr.gs/TheAmazonCodingDemo) — Amazon's free OA practice test 🚀


https://www.amazon.jobs/content/en/how-we-hire/interview-prep/software-development-topics

## 📋 All 10 Topics Amazon Says to Prepare

---

### 1️⃣ Programming Language

Your Java basically. They want you to know it well enough to code without an IDE.

What to know:

- Arrays, ArrayLists, HashMaps, HashSets
- String methods (`.split()`, `.charAt()`, `.substring()`)
- Loops, conditionals, recursion
- Basic OOP (classes, objects, methods)

---

### 2️⃣ Data Structures

The **biggest** topic. Most OA and interview questions are from here.

|Structure|What to know|
|---|---|
|Arrays|Traversal, subarray, rotation|
|Strings|Palindrome, anagram, reversal|
|LinkedList|Reverse, cycle detection, merge|
|Stack|Valid parentheses, min stack|
|Queue|BFS, sliding window|
|HashMap|Frequency count, two sum|
|Trees|Traversal, height, LCA|
|Graphs|BFS, DFS, number of islands|
|Heap/PriorityQueue|Top K elements|

---

### 3️⃣ Algorithms

The patterns you apply to solve problems.

|Algorithm|Example Problem|
|---|---|
|Two Pointers|3Sum, Container with most water|
|Sliding Window|Longest substring, max sum|
|Binary Search|Search in rotated array|
|BFS/DFS|Island count, shortest path|
|Dynamic Programming|Climbing stairs, coin change|
|Recursion|Fibonacci, subsets|
|Sorting|Merge sort, quick sort basics|

---

### 4️⃣ Coding

They recommend practicing coding outside of an integrated development environment — meaning get used to writing on LeetCode or plain editor, not IntelliJ.

They look for:

- Clean readable code
- Correct logic
- Edge cases handled
- Time & space complexity explained

---

### 5️⃣ Object Oriented Design

This is for the **system design / Loop rounds**.

What to know:

- Classes & Objects
- Inheritance, Encapsulation, Polymorphism, Abstraction
- Design patterns (basic ones — Singleton, Factory)

Example questions:

- Design a Parking Lot class
- Design a Library system
- Design a Vending Machine

---

### 6️⃣ Databases

Basic SQL knowledge needed.

What to know:

- SELECT, WHERE, JOIN, GROUP BY, ORDER BY
- Primary keys, Foreign keys
- Basic indexing concept
- Difference between SQL and NoSQL

Example question: _"Design tables for an e-commerce order system"_

---

### 7️⃣ Distributed Computing

High level concepts — mostly for Loop rounds, not OA.

What to know (just concepts, not deep):

- What is a distributed system?
- Load balancing
- CAP theorem (Consistency, Availability, Partition tolerance)
- Caching basics (what is Redis?)
- Horizontal vs vertical scaling

---

### 8️⃣ Operating Systems

Basic OS concepts — rarely asked for SDE I but good to know.

What to know:

- Processes vs Threads
- Deadlock (what it is, how to avoid)
- Memory management basics
- Mutex, Semaphores

---

### 9️⃣ Internet Topics

Web basics — more important than people think.

What to know:

- How HTTP/HTTPS works
- What is REST API?
- GET vs POST
- DNS basics
- What happens when you type google.com?

---

### 🔟 Machine Learning & AI

Least important for SDE I. Just be aware of basics.

What to know:

- What is ML? Supervised vs Unsupervised
- What is a neural network (basic idea)
- You won't be asked to code ML algorithms

---

## 🎯 Priority Order for YOU (SDE I Fresher)

```
🔴 Must master    → Data Structures + Algorithms + Coding
🟠 Important      → OOP + Databases + Internet Topics  
🟡 Good to know   → Distributed Computing + OS
🟢 Just be aware  → ML/AI
```

Start with the 🔴 ones — that's 80% of your OA and interview! 🚀

https://drive.google.com/file/d/1BXOGryuaqGCJicHp6hG6aB-T8mMO2ZUe/view


check these for guides:
