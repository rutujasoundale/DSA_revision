# DSA Revision Roadmap — Pattern
**Target:** Service-based & mass-recruiter placements (TCS NQT/CodeVita, Capgemini, Cognizant, Deloitte NLA, Infosys, Wipro, etc.)
**Timeline:** 8 weeks | **Pace:** 4 hrs/day | **Platform:** LeetCode , GFG

---

## How to use this roadmap

You've already covered Arrays/Strings, Hashmaps, Sorting, Searching, and basic Stacks/Queues. This plan does **not** re-teach those from scratch — it revises them through patterns, layers in the patterns you haven't touched (Two Pointers, Sliding Window, Linked List, Trees, Graphs, DP, Greedy, Bit Manipulation), and pushes **Recursion to the end** as you asked, since Backtracking/DP depend on it anyway so it flows naturally into those.

For service-based companies specifically: the coding rounds (TCS NQT/CodeVita, Cognizant GenC, Capgemini Pseudocode, Deloitte NLA) rarely ask Hard-tier problems. They lean on Easy–Medium array/string/math/pattern questions, output-prediction, and a handful of standard patterns (two pointers, sliding window, basic recursion, basic DP, basic graph traversal). So this roadmap is breadth-first: cover every pattern at least once, get 70-80% comfortable, rather than mastering Hard DP/Graph problems. A "Service-Based Priority ⭐" tag marks problems that show up most often in these specific tests.

Each week: **Concept revision → Pattern recognition → 8-12 problems → 1 mock/timed set**.

---

## Week 1 — Arrays, Strings & Two Pointers (Revision + New Pattern)
1-2july
### Day-wise breakdown
**Day 1-2: Array/String quick revision**
Skim your old notes on traversal, prefix sums, basic string manipulation. Don't re-solve everything — just refresh.
- Two Sum ⭐ (Easy)
- Best Time to Buy and Sell Stock ⭐ (Easy)
- Maximum Subarray (Kadane's Algorithm) ⭐ (Medium)
- Product of Array Except Self (Medium)
3-4 july
**Day 3-4: Two Pointers pattern (new)**
Core idea: use two indices moving toward/away from each other to avoid nested loops (O(n) instead of O(n²)).
- Valid Palindrome ⭐ (Easy)
- Two Sum II - Input Array Is Sorted (Easy)
- 3Sum ⭐ (Medium)
- Container With Most Water ⭐ (Medium)
- Sort Colors (Dutch National Flag) (Medium)
- Trapping Rain Water (Hard — attempt only if time permits)
5 july
**Day 5: Sliding Window pattern (new)**
Core idea: maintain a window of elements, expand/shrink based on a condition. Used for subarray/substring problems.
- Maximum Average Subarray I (Easy)
- Longest Substring Without Repeating Characters ⭐ (Medium)
- Minimum Size Subarray Sum (Medium)
- Longest Repeating Character Replacement (Medium)
6 july
**Day 6: String revision + pattern overlap**
- Valid Anagram ⭐ (Easy)
- Group Anagrams ⭐ (Medium)
- Longest Common Prefix ⭐ (Easy)
- String Compression (Medium)
7 july
**Day 7: Timed mock (1.5-2 hrs) + revise weak spots**
Pick 4 random problems from the week, solve under time pressure.

---
2nd week of july
## Week 2 — Hashmaps, Sorting/Searching Patterns + Matrix

**Day 1: Hashmap pattern revision**
Core idea: O(1) lookup to convert nested loops into single pass.
- Contains Duplicate (Easy)
- Top K Frequent Elements ⭐ (Medium)
- Subarray Sum Equals K ⭐ (Medium) — prefix sum + hashmap combo, very common
- Longest Consecutive Sequence (Medium)

**Day 2: Sorting-based patterns**
Core idea: sort first, then apply two-pointer/greedy logic.
- Merge Intervals ⭐ (Medium)
- Insert Interval (Medium)
- Non-overlapping Intervals (Medium)
- Meeting Rooms II (concept — may need premium/GFG equivalent)

**Day 3: Binary Search pattern (revision + variants)**
Core idea: not just "search a sorted array" — also search-space reduction problems.
- Binary Search ⭐ (Easy)
- Search in Rotated Sorted Array ⭐ (Medium)
- Find Minimum in Rotated Sorted Array (Medium)
- Search a 2D Matrix ⭐ (Medium)

**Day 4: Matrix pattern (new, common in service-based tests)**
- Rotate Image (Medium)
- Spiral Matrix ⭐ (Medium)
- Set Matrix Zeroes (Medium)

**Day 5-6: Mixed array/string/hashmap problems frequently seen in NQT/Capgemini/Cognizant**
- Move Zeroes ⭐ (Easy)
- Majority Element ⭐ (Easy)
- Next Permutation (Medium)
- Pascal's Triangle (Easy)
- Rotate Array (Easy)

**Day 7: Timed mock + revise**

---

## Week 3 july — Stacks, Queues & Linked Lists

**Day 1-2: Stack pattern (you know basics — go deeper)**
Core idea: track "next greater/smaller", balanced structures, undo operations.
- Valid Parentheses ⭐ (Easy)
- Min Stack ⭐ (Medium)
- Daily Temperatures ⭐ (Medium) — Monotonic stack pattern
- Next Greater Element I (Easy)
- Evaluate Reverse Polish Notation (Medium)

**Day 3: Queue pattern**
- Implement Queue using Stacks (Easy)
- Sliding Window Maximum (Hard — concept matters more than solving it cold; uses monotonic deque)
- Design Circular Queue (Medium)

**Day 4-5: Linked List pattern (new)**
Core idea: pointer manipulation — fast/slow pointers, reversal, dummy nodes.
- Reverse Linked List ⭐ (Easy)
- Merge Two Sorted Lists ⭐ (Easy)
- Linked List Cycle ⭐ (Easy) — Floyd's cycle detection
- Remove Nth Node From End of List ⭐ (Medium)
- Reorder List (Medium)
- Add Two Numbers ⭐ (Medium)
- Copy List with Random Pointer (Medium)

**Day 6: LL + Stack mixed review**
- Palindrome Linked List (Easy)
- Intersection of Two Linked Lists (Easy)

**Day 7: Timed mock + revise**

---

## Week 4 july — Trees & Binary Search Trees

**Day 1-2: Tree traversal pattern (foundation)**
Core idea: DFS (pre/in/post-order) and BFS (level order) — almost every tree problem builds on these.
- Binary Tree Inorder Traversal ⭐ (Easy)
- Maximum Depth of Binary Tree ⭐ (Easy)
- Binary Tree Level Order Traversal ⭐ (Medium)
- Same Tree (Easy)
- Invert Binary Tree ⭐ (Easy)

**Day 3-4: BST-specific pattern**
Core idea: leverage sorted property for O(log n) operations.
- Validate Binary Search Tree ⭐ (Medium)
- Lowest Common Ancestor of a BST ⭐ (Medium)
- Insert into a Binary Search Tree (Medium)
- Kth Smallest Element in a BST (Medium)
- Convert Sorted Array to BST (Easy)

**Day 5: Tree + recursion overlap (light intro before full recursion week)**
- Diameter of Binary Tree ⭐ (Easy)
- Balanced Binary Tree (Easy)
- Path Sum (Easy)
- Symmetric Tree (Easy)

**Day 6: Advanced tree (lighter, only if comfortable)**
- Construct Binary Tree from Preorder and Inorder Traversal (Medium)
- Serialize and Deserialize Binary Tree (Hard — optional)

**Day 7: Timed mock + revise**

---

## Week 5 july-aug— Graphs (BFS/DFS) + Heaps

**Day 1-2: Graph traversal pattern (new, important for Deloitte/Cognizant)**
Core idea: represent as adjacency list, then BFS for shortest path/levels, DFS for connectivity/cycles.
- Number of Islands ⭐ (Medium) — DFS/BFS on grid, extremely common
- Flood Fill ⭐ (Easy)
- Clone Graph (Medium)
- Course Schedule ⭐ (Medium) — topological sort / cycle detection
- Rotting Oranges (Medium) — multi-source BFS

**Day 3: Graph continued**
- Pacific Atlantic Water Flow (Medium)
- Number of Connected Components in an Undirected Graph (Medium)
- Graph Valid Tree (Medium)

**Day 4-5: Heap / Priority Queue pattern (new)**
Core idea: get min/max efficiently, used for "Kth largest/smallest" and scheduling problems.
- Kth Largest Element in an Array ⭐ (Medium)
- Top K Frequent Elements (revisit with heap approach)
- Find Median from Data Stream (Hard — concept only if time-strapped)
- Task Scheduler (Medium)
- Merge K Sorted Lists (Hard — attempt with heap, very common interview ask)

**Day 6: Mixed graph/heap review + GFG-style output problems**
Service-based tests love "predict the output of this BFS/DFS traversal" — practice tracing by hand, not just coding.

**Day 7: Timed mock + revise**

---

## Week 6 — Dynamic Programming (1D & 2D) + Greedy
2nd week of aug
**Day 1-2: 1D DP pattern (core)**
Core idea: break problem into subproblems, store results (memoization/tabulation) to avoid recomputation.
- Climbing Stairs ⭐ (Easy) — the gateway DP problem
- House Robber ⭐ (Medium)
- Coin Change ⭐ (Medium)
- Longest Increasing Subsequence ⭐ (Medium)
- Maximum Subarray (revisit as DP, you did it as Kadane's in Week 1)
- Word Break (Medium)

**Day 3-4: 2D DP pattern**
Core idea: state depends on two indices — grids, two strings.
- Unique Paths ⭐ (Medium)
- Longest Common Subsequence ⭐ (Medium)
- Edit Distance (Medium)
- 0/1 Knapsack (GFG classic — foundational for many MNC questions) ⭐
- Coin Change II (Medium)

**Day 5: Greedy pattern (new)**
Core idea: make the locally optimal choice at each step; works when problems have the greedy-choice property.
- Jump Game ⭐ (Medium)
- Gas Station (Medium)
- Maximum Subarray (greedy lens revisit)
- Activity Selection (GFG classic, common in service-based tests) ⭐

**Day 6: Mixed DP/Greedy review**
Trace through 4-5 DP problems on paper (draw the table) — this is what helps in timed/pseudocode rounds like Capgemini's.

**Day 7: Timed mock + revise**

---
Aug(week2-3)
## Week 7 — Bit Manipulation + Recursion & Backtracking

**Day 1: Bit Manipulation pattern (new, frequent in TCS/Cognizant aptitude-adjacent rounds)**
- Single Number ⭐ (Easy)
- Number of 1 Bits ⭐ (Easy)
- Counting Bits (Easy)
- Reverse Bits (Easy)
- Missing Number ⭐ (Easy) — XOR trick

**Day 2-3: Recursion fundamentals (your requested placement — now we build it up properly)**
Core idea: a function calling itself on a smaller subproblem, with a base case to stop.
- Fibonacci Number ⭐ (Easy)
- Power of x to n (fast exponentiation) ⭐ (Medium)
- Generate Parentheses ⭐ (Medium)
- Factorial / Sum of Digits (basic warm-up, GFG)
- Reverse a String/Array using recursion (Easy)

**Day 4-5: Backtracking pattern (recursion's main application)**
Core idea: build a solution incrementally, abandon ("backtrack") paths that fail constraints.
- Subsets ⭐ (Medium)
- Permutations ⭐ (Medium)
- Combination Sum ⭐ (Medium)
- Letter Combinations of a Phone Number ⭐ (Medium)
- N-Queens (Hard — concept walkthrough is enough)
- Word Search (Medium)
aug(3)
**Day 6: Recursion + DP/Tree connection**
Recursion ties back into everything: revisit 2-3 tree problems and 2-3 DP problems, but this time write the recursive solution before the optimized one — this builds the intuition interviewers actually probe for.

**Day 7: Timed mock + revise**

---
August Week 4
## Week 8 — Full Revision, Mocks & Company-Specific Prep

**Day 1-2: Pattern-recall drill**
Without looking at notes, write down (on paper) for each pattern: when to use it + one example problem. This active-recall step matters more than solving new problems at this stage.

**Day 3-4: Company-specific practice**
- TCS NQT/CodeVita: focus on output-prediction, basic-medium array/string, simple recursion, time-boxed problems (15-20 min each)
- Capgemini Pseudocode: practice converting pseudocode to code and vice versa; revise sorting/searching by hand-tracing
- Cognizant GenC: medium array/string + 1-2 DP/graph
- Deloitte NLA/NQT: slightly higher bar — revisit Medium-tier two pointers, sliding window, trees, graphs

**Day 5-6: Full-length timed mocks**
Simulate real conditions: 60-90 minutes, 2-3 problems, no notes. Use LeetCode's contest mode or pick problems cold from a shuffled list across all patterns.

**Day 7: Final review**
Revisit only the problems you got wrong or struggled with across all 8 weeks. Don't start anything new.

---

## Pattern → Problem-Type Cheat Sheet (quick mental map)

| Pattern | Use When You See... | Time Complexity Goal |
|---|---|---|
| Two Pointers | Sorted array, pair/triplet sum, palindrome check | O(n) |
| Sliding Window | Subarray/substring with a condition (max/min length, sum) | O(n) |
| Hashmap | Need O(1) lookup, frequency counting, "have I seen this before" | O(n) |
| Binary Search | Sorted array, or "search space" can be halved | O(log n) |
| Monotonic Stack | "Next greater/smaller element", histogram problems | O(n) |
| Fast & Slow Pointers (LL) | Cycle detection, middle of list | O(n) |
| Tree DFS/BFS | Any tree problem — traversal, depth, path | O(n) |
| Graph BFS | Shortest path, level-by-level, multi-source spread | O(V+E) |
| Graph DFS | Connectivity, cycle detection, islands | O(V+E) |
| Heap | "Kth largest/smallest", merging sorted structures, scheduling | O(n log k) |
| 1D DP | "Number of ways", "min/max cost", single array dependency | O(n) |
| 2D DP | Two strings/sequences, grid paths, knapsack-style | O(n×m) |
| Greedy | "Maximum/minimum with local optimal choice", intervals | O(n log n) |
| Backtracking | "All possible combinations/permutations/subsets" | Exponential (bounded by constraints) |
| Bit Manipulation | XOR tricks, single number, power-of-2 checks | O(1) or O(log n) |

---

## Service-Based Company Notes (quick reference)

- **TCS NQT/CodeVita:** 2-3 coding questions, Easy-Medium, often basic array/string/math/recursion. Speed matters more than elegance. Practice typing fast and handling edge cases (empty input, negative numbers).
- **Capgemini:** Often includes a "Pseudocode" section — practice reading pseudocode and converting it to code, and vice versa. Coding questions are usually Easy-Medium.
- **Cognizant GenC/GenC Next:** GenC Next has a slightly higher bar — expect 1-2 Medium DP or graph problems alongside basics.
- **Deloitte NLA/NQT:** Tends to test logical/analytical ability alongside coding — comfortable with trees, graphs, and basic DP gives you an edge over peers who only know arrays.
- **General tip across all:** these companies weight CS fundamentals (OOPs, DBMS, OS, CN) and aptitude alongside DSA — this roadmap covers DSA only, budget separate time for those if your specific application requires them.

---

## Progress Tracker

Use this simple checklist format to mark weeks as done:

- [ ] Week 1 — Arrays, Strings, Two Pointers, Sliding Window
- [ ] Week 2 — Hashmaps, Sorting, Binary Search, Matrix
- [ ] Week 3 — Stacks, Queues, Linked Lists
- [ ] Week 4 — Trees & BST
- [ ] Week 5 — Graphs & Heaps
- [ ] Week 6 — Dynamic Programming & Greedy
- [ ] Week 7 — Bit Manipulation, Recursion & Backtracking
- [ ] Week 8 — Full Revision & Company-Specific Mocks
