# Java HashMap & HashSet — DSA Interview Notes

HashMap and HashSet are extremely important for Java DSA interviews.

They are especially useful for:

- Counting frequencies
- Checking whether an element exists
- Finding duplicates
- Two Sum
- Anagrams
- Grouping elements
- Finding first/unique elements
- Mapping one value to another

---

# 1. HashMap Basics

## What is a HashMap?

A `HashMap` stores data in **key-value pairs**.

```text
Key → Value
```

Example:

```text
1 → Alice
2 → Bob
3 → Charlie
```

In Java:

```java
Map<Integer, String> map = new HashMap<>();
```

Here:

- `Integer` = key type
- `String` = value type

### Important properties

| Property | HashMap |
|---|---|
| Stores | Key-value pairs |
| Duplicate keys | ❌ No |
| Duplicate values | ✅ Yes |
| Maintains insertion order | ❌ No |
| Allows one null key | ✅ Yes |
| Allows null values | ✅ Yes |
| Average lookup | O(1) |
| Worst-case lookup | O(n)* |

\*Modern Java HashMap can convert heavily-colliding buckets into balanced trees, making some worst-case operations O(log n), but for normal interview analysis, use **average O(1)** unless the question specifically asks about HashMap internals.

---

# 2. Basic HashMap Operations

```java
import java.util.HashMap;
import java.util.Map;

public class HashMapBasic {

    public static void main(String[] args) {

        Map<Integer, String> map = new HashMap<>();

        // Insert
        map.put(1, "Alice");
        map.put(2, "Bob");
        map.put(3, "Charlie");

        // Get value
        System.out.println(map.get(2));

        // Check key
        System.out.println(map.containsKey(3));

        // Update
        map.put(2, "Bobby");

        // Remove
        map.remove(1);

        // Size
        System.out.println(map.size());

        // Iterate
        for (Map.Entry<Integer, String> entry : map.entrySet()) {
            System.out.println(
                entry.getKey() + " -> " + entry.getValue()
            );
        }
    }
}
```

---

# 3. Important HashMap Methods

```java
Map<String, Integer> map = new HashMap<>();
```

### Insert

```java
map.put("A", 1);
```

Result:

```text
A → 1
```

### Get

```java
map.get("A");
```

Returns:

```text
1
```

### Check key

```java
map.containsKey("A");
```

Returns:

```text
true
```

### Remove

```java
map.remove("A");
```

### Size

```java
map.size();
```

### Check whether empty

```java
map.isEmpty();
```

### Get with default value

```java
map.getOrDefault("A", 0);
```

If `"A"` exists:

```text
returns its value
```

If `"A"` doesn't exist:

```text
returns 0
```

This is extremely useful for **frequency counting**.

---

# 4. HashMap Time Complexity

| Operation | Average | Worst Case |
|---|---:|---:|
| `put()` | O(1) | O(log n) / implementation-dependent |
| `get()` | O(1) | O(log n) / implementation-dependent |
| `containsKey()` | O(1) | O(log n) / implementation-dependent |
| `remove()` | O(1) | O(log n) / implementation-dependent |
| `size()` | O(1) | O(1) |

For most placement DSA questions:

> **HashMap lookup = O(1) average**

---

# 5. Pattern 1 — Frequency Counting

One of the **most important HashMap patterns**.

## Problem

Given:

```text
[1, 2, 3, 2, 1, 2, 4]
```

Find how many times each number occurs.

Expected:

```text
1 → 2
2 → 3
3 → 1
4 → 1
```

## Code

```java
import java.util.HashMap;
import java.util.Map;

public class FrequencyCount {

    public static void main(String[] args) {

        int[] nums = {1, 2, 3, 2, 1, 2, 4};

        Map<Integer, Integer> freq = new HashMap<>();

        for (int x : nums) {

            freq.put(
                x,
                freq.getOrDefault(x, 0) + 1
            );
        }

        for (Map.Entry<Integer, Integer> entry : freq.entrySet()) {

            System.out.println(
                entry.getKey() +
                " occurs " +
                entry.getValue() +
                " times"
            );
        }
    }
}
```

---

## Understanding the Main Line

```java
freq.put(x, freq.getOrDefault(x, 0) + 1);
```

This means:

> Get the current frequency of `x`, and increase it by 1.

Suppose:

```text
x = 2
```

If `2` does not exist:

```java
freq.getOrDefault(2, 0)
```

returns:

```text
0
```

Then:

```text
0 + 1 = 1
```

So:

```text
2 → 1
```

Next time `2` appears:

```text
2 → 2
```

Next:

```text
2 → 3
```

---

# 6. Frequency Count Dry Run

Input:

```text
[1, 2, 3, 2, 1, 2, 4]
```

Start:

```text
{}
```

### Step 1

`x = 1`

```text
1 doesn't exist
0 + 1 = 1
```

Map:

```text
{1=1}
```

### Step 2

`x = 2`

```text
{1=1, 2=1}
```

### Step 3

`x = 3`

```text
{1=1, 2=1, 3=1}
```

### Step 4

`x = 2`

Existing frequency:

```text
2 → 1
```

Increase:

```text
1 + 1 = 2
```

Map:

```text
{1=1, 2=2, 3=1}
```

### Step 5

`x = 1`

```text
1 → 2
```

### Step 6

`x = 2`

```text
2 → 3
```

### Step 7

`x = 4`

```text
4 → 1
```

Final:

```text
1 → 2
2 → 3
3 → 1
4 → 1
```

---

## Complexity

Let `n` = number of elements.

### Time

We visit every element once:

```text
O(n)
```

Each HashMap operation is O(1) average.

### Space

In the worst case, every element is different:

```text
O(n)
```

Therefore:

```text
Time:  O(n)
Space: O(n)
```

---

# 7. HashSet

## What is HashSet?

A `HashSet` stores **unique values only**.

Unlike HashMap:

```text
HashMap → key + value

HashSet → only values
```

Example:

```java
Set<Integer> set = new HashSet<>();
```

If we insert:

```text
1
2
3
2
1
```

The Set contains:

```text
1
2
3
```

Duplicates are automatically ignored.

---

# 8. HashSet Duplicate Check

## Problem

Determine whether an array contains a duplicate.

Input:

```text
[1, 2, 3, 4, 2]
```

Output:

```text
Duplicate found: 2
```

## Code

```java
import java.util.HashSet;
import java.util.Set;

public class DuplicateCheck {

    public static void main(String[] args) {

        int[] nums = {1, 2, 3, 4, 2};

        Set<Integer> seen = new HashSet<>();

        for (int x : nums) {

            if (seen.contains(x)) {

                System.out.println(
                    "Duplicate found: " + x
                );

                return;
            }

            seen.add(x);
        }

        System.out.println("No duplicates");
    }
}
```

---

# 9. Duplicate Check Dry Run

Input:

```text
[1, 2, 3, 4, 2]
```

Initially:

```text
seen = {}
```

### 1

`1` not present.

Add:

```text
{1}
```

### 2

`2` not present.

```text
{1, 2}
```

### 3

```text
{1, 2, 3}
```

### 4

```text
{1, 2, 3, 4}
```

### 2 again

Check:

```java
seen.contains(2)
```

Result:

```text
true
```

Therefore:

```text
Duplicate found: 2
```

---

## Complexity

We traverse the array once.

```text
Time: O(n)
Space: O(n)
```

---

# 10. HashMap vs HashSet

| Feature | HashMap | HashSet |
|---|---|---|
| Stores | Key-value | Values |
| Duplicate values | Allowed | Not allowed |
| Duplicate keys | Not allowed | N/A |
| Main use | Mapping/counting | Presence/uniqueness |
| Example | Number → frequency | Seen numbers |

### Simple rule

Ask yourself:

> **Do I need to store information about an element?**

If yes:

```text
HashMap
```

Example:

```text
number → frequency
number → index
character → frequency
```

If you only need:

> **Have I seen this before?**

Use:

```text
HashSet
```

---

# 11. Pattern 2 — Two Sum

One of the most famous HashMap interview problems.

## Problem

Given:

```text
nums = [2, 7, 11, 15]
target = 9
```

Find two numbers whose sum equals the target.

```text
2 + 7 = 9
```

Answer:

```text
indices = [0, 1]
```

---

# 12. Brute Force Approach

You could use two loops:

```java
for (int i = 0; i < n; i++) {

    for (int j = i + 1; j < n; j++) {

        if (nums[i] + nums[j] == target) {
            // answer
        }
    }
}
```

Complexity:

```text
Time: O(n²)
Space: O(1)
```

But we can do better using HashMap.

---

# 13. HashMap Two Sum

```java
import java.util.HashMap;
import java.util.Map;

public class TwoSum {

    public static void main(String[] args) {

        int[] nums = {2, 7, 11, 15};
        int target = 9;

        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {

            int current = nums[i];

            int needed = target - current;

            if (map.containsKey(needed)) {

                System.out.println(
                    "Pair found at indices: " +
                    map.get(needed) +
                    " and " +
                    i
                );

                return;
            }

            map.put(current, i);
        }

        System.out.println("No pair found");
    }
}
```

---

# 14. Two Sum — Core Idea

The important formula is:

```text
needed = target - current
```

Suppose:

```text
target = 9
current = 7
```

Then:

```text
needed = 9 - 7
needed = 2
```

So we ask:

> Have I already seen 2?

If yes:

```text
2 + 7 = 9
```

We found the answer.

---

# 15. Two Sum Dry Run

Input:

```text
nums = [2, 7, 11, 15]
target = 9
```

Initially:

```text
map = {}
```

### i = 0

```text
current = 2
needed = 9 - 2 = 7
```

Is `7` in map?

```text
No
```

Store:

```text
2 → 0
```

Map:

```text
{2=0}
```

---

### i = 1

```text
current = 7
needed = 9 - 7 = 2
```

Is `2` present?

```text
Yes
```

Map tells us:

```text
2 → index 0
```

Current index:

```text
1
```

Therefore:

```text
[0, 1]
```

---

## Complexity

We scan the array once.

```text
Time: O(n)
Space: O(n)
```

This improves the brute-force:

```text
O(n²) → O(n)
```

---

# 16. Pattern 3 — Anagram

## What is an anagram?

Two strings are anagrams if they contain the same characters with the same frequencies.

Example:

```text
listen
silent
```

Both contain:

```text
l → 1
i → 1
s → 1
t → 1
e → 1
n → 1
```

Therefore:

```text
Anagram
```

---

# 17. Anagram Using HashMap

```java
import java.util.HashMap;
import java.util.Map;

public class AnagramCheck {

    public static void main(String[] args) {

        String s1 = "listen";
        String s2 = "silent";

        if (s1.length() != s2.length()) {
            System.out.println("Not anagram");
            return;
        }

        Map<Character, Integer> freq = new HashMap<>();

        // Count characters of first string
        for (char ch : s1.toCharArray()) {

            freq.put(
                ch,
                freq.getOrDefault(ch, 0) + 1
            );
        }

        // Remove characters using second string
        for (char ch : s2.toCharArray()) {

            if (!freq.containsKey(ch)) {
                System.out.println("Not anagram");
                return;
            }

            freq.put(ch, freq.get(ch) - 1);

            if (freq.get(ch) == 0) {
                freq.remove(ch);
            }
        }

        System.out.println(
            freq.isEmpty()
            ? "Anagram"
            : "Not anagram"
        );
    }
}
```

---

# 18. Anagram Dry Run

```text
s1 = "listen"
s2 = "silent"
```

First count `s1`:

```text
l → 1
i → 1
s → 1
t → 1
e → 1
n → 1
```

Now process `"silent"`.

### s

```text
s → 1 → 0
```

Remove `s`.

### i

```text
i → 1 → 0
```

Remove `i`.

Continue for:

```text
l
e
n
t
```

Eventually:

```text
{}
```

The map is empty.

Therefore:

```text
Anagram
```

---

## Complexity

Let `n` be the string length.

We process each string once:

```text
Time: O(n)
Space: O(k)
```

where `k` is the number of distinct characters.

If the character set is fixed, such as lowercase English letters:

```text
k ≤ 26
```

So space can effectively be considered:

```text
O(1)
```

---

# 19. Pattern 4 — Group Anagrams

## Problem

Given:

```text
["eat", "tea", "tan", "ate", "nat", "bat"]
```

Group the anagrams.

Expected:

```text
[
    ["eat", "tea", "ate"],
    ["tan", "nat"],
    ["bat"]
]
```

---

# 20. Main Idea — Create a Signature

For every word, sort its characters.

```text
eat → aet
tea → aet
ate → aet
```

Therefore all three get the same key:

```text
"aet"
```

Similarly:

```text
tan → ant
nat → ant
```

So:

```text
ant → [tan, nat]
```

---

# 21. Code

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class GroupAnagrams {

    public static void main(String[] args) {

        String[] words = {
            "eat", "tea", "tan",
            "ate", "nat", "bat"
        };

        Map<String, List<String>> map =
            new HashMap<>();

        for (String word : words) {

            char[] chars = word.toCharArray();

            Arrays.sort(chars);

            String key = new String(chars);

            if (!map.containsKey(key)) {
                map.put(key, new ArrayList<>());
            }

            map.get(key).add(word);
        }

        System.out.println(map);
    }
}
```

---

# 22. Group Anagrams Dry Run

### `eat`

Sort:

```text
eat → aet
```

Map:

```text
aet → [eat]
```

### `tea`

```text
tea → aet
```

Map:

```text
aet → [eat, tea]
```

### `tan`

```text
tan → ant
```

Map:

```text
aet → [eat, tea]
ant → [tan]
```

### `ate`

```text
ate → aet
```

Map:

```text
aet → [eat, tea, ate]
ant → [tan]
```

### `nat`

```text
nat → ant
```

Map:

```text
aet → [eat, tea, ate]
ant → [tan, nat]
```

### `bat`

```text
bat → abt
```

Final:

```text
aet → [eat, tea, ate]
ant → [tan, nat]
abt → [bat]
```

---

## Complexity

Suppose:

- `n` = number of strings
- `k` = average length of each string

Sorting each string costs:

```text
O(k log k)
```

For `n` strings:

```text
Time: O(n × k log k)
```

Space:

```text
O(n × k)
```

because we store the strings in groups.

---

# 23. Pattern 5 — First Non-Repeating Character

## Problem

Given:

```text
"aabccdeff"
```

Find the first character that occurs only once.

Answer:

```text
b
```

---

# 24. Approach

Use two passes.

### Pass 1

Count frequency of every character.

### Pass 2

Scan the original string from left to right.

The first character with:

```text
frequency == 1
```

is the answer.

---

# 25. Code

```java
import java.util.HashMap;
import java.util.Map;

public class FirstNonRepeating {

    public static void main(String[] args) {

        String s = "aabccdeff";

        Map<Character, Integer> freq =
            new HashMap<>();

        // Pass 1: frequency count
        for (char ch : s.toCharArray()) {

            freq.put(
                ch,
                freq.getOrDefault(ch, 0) + 1
            );
        }

        // Pass 2: find first unique character
        for (char ch : s.toCharArray()) {

            if (freq.get(ch) == 1) {

                System.out.println(
                    "First non-repeating character: " + ch
                );

                return;
            }
        }

        System.out.println(
            "No non-repeating character"
        );
    }
}
```

---

# 26. Dry Run

String:

```text
aabccdeff
```

Frequency:

```text
a → 2
b → 1
c → 2
d → 1
e → 1
f → 2
```

Now scan again:

```text
a → frequency 2 ❌
a → frequency 2 ❌
b → frequency 1 ✅
```

Answer:

```text
b
```

---

## Complexity

```text
Time: O(n)
Space: O(k)
```

where `k` = number of distinct characters.

For a fixed alphabet:

```text
Space ≈ O(1)
```

---

# 27. Most Important HashMap Patterns

For placements, don't just memorize individual questions.

Learn these **patterns**.

| Pattern | Data Structure |
|---|---|
| Frequency counting | HashMap |
| Check duplicate | HashSet |
| Check presence | HashSet |
| Number → frequency | HashMap |
| Number → index | HashMap |
| Character → frequency | HashMap |
| Two Sum | HashMap |
| Anagram | HashMap |
| Group Anagrams | HashMap |
| First unique element | HashMap |
| Prefix sum + target | HashMap |

---

# 28. The Most Important Mental Template

Whenever you see:

> "How many times does each element occur?"

Think:

```java
Map<Integer, Integer> freq = new HashMap<>();

for (int x : nums) {
    freq.put(x, freq.getOrDefault(x, 0) + 1);
}
```

---

Whenever you see:

> "Have I seen this element before?"

Think:

```java
Set<Integer> seen = new HashSet<>();

if (seen.contains(x)) {
    // duplicate
}

seen.add(x);
```

---

Whenever you see:

> "Find two elements that satisfy some target"

Think:

```text
needed = target - current
```

Then check:

```java
map.containsKey(needed)
```

---

# 29. HashMap + Prefix Sum Pattern

This is a slightly more advanced pattern and is worth learning after Two Sum.

Example problem:

> Count the number of subarrays whose sum equals `k`.

The basic idea is:

```text
prefixSum - k
```

If this value has appeared before, a subarray with sum `k` exists.

This uses:

```text
HashMap + Prefix Sum
```

This pattern appears in many coding interviews.

---

# 30. Common Interview Questions

## Easy Level

### Q1. Count frequency of elements

Input:

```text
[1,2,2,3,3,3]
```

Output:

```text
1 → 1
2 → 2
3 → 3
```

Pattern:

```text
HashMap + frequency
```

---

### Q2. Find duplicates

Input:

```text
[1,2,3,2]
```

Output:

```text
2
```

Pattern:

```text
HashSet
```

---

### Q3. Check if two strings are anagrams

```text
listen
silent
```

Output:

```text
true
```

Pattern:

```text
HashMap / frequency
```

---

### Q4. First non-repeating character

```text
aabbcdde
```

Output:

```text
c
```

Pattern:

```text
Frequency Map + second scan
```

---

# 31. Medium-Level Interview Questions

### Q5. Two Sum

```text
nums = [2,7,11,15]
target = 9
```

Output:

```text
[0,1]
```

Pattern:

```text
HashMap
```

---

### Q6. Group Anagrams

```text
["eat","tea","tan","ate","nat","bat"]
```

Output:

```text
[
 ["eat","tea","ate"],
 ["tan","nat"],
 ["bat"]
]
```

Pattern:

```text
HashMap + sorted signature
```

---

### Q7. Find the element with maximum frequency

Example:

```text
[1,2,2,3,2,4]
```

Output:

```text
2
```

Approach:

```text
1. Build frequency map
2. Find maximum frequency
```

Complexity:

```text
Time: O(n)
Space: O(n)
```

---

# 32. Placement-Oriented PYQs / Commonly Asked Questions

For **TCS, Capgemini, Cognizant, Infosys, Wipro and similar service-based placements**, these are the kinds of HashMap/HashSet problems worth practicing.

> Exact wording and difficulty can vary by hiring test and year, so treat these as recurring/common placement patterns rather than assuming a particular question will appear in your test.

### TCS-style practice

1. Count frequency of characters in a string.
2. Find duplicate elements in an array.
3. Find the first non-repeating character.
4. Check whether two strings are anagrams.
5. Find the frequency of each number.
6. Find the most frequent element.

### Cognizant-style practice

1. Remove duplicate elements.
2. Find the first repeated element.
3. Find the first non-repeating character.
4. Check whether two strings contain the same characters.
5. Count occurrences of words.
6. Find common elements between arrays.

### Capgemini-style practice

1. Frequency counting.
2. Duplicate detection.
3. Anagram checking.
4. Find unique elements.
5. Find pairs with a given sum.
6. Count occurrences of characters/words.

### Infosys-style practice

1. Character frequency.
2. Duplicate detection.
3. Two Sum / pair-sum variations.
4. First unique character.
5. Common elements.
6. Frequency-based array problems.

### Wipro / Deloitte / other service-based practice

Focus on:

```text
Frequency Map
HashSet
Two Sum
Anagram
Duplicates
Unique elements
Maximum frequency
Prefix Sum + HashMap
```

---

# 33. Practice Set — Solve Without Looking at the Solution

## Level 1

### Problem 1 — Frequency

Given:

```text
int[] nums = {1,2,2,3,3,3,4};
```

Print:

```text
1 → 1
2 → 2
3 → 3
4 → 1
```

---

### Problem 2 — Duplicate

Given:

```text
int[] nums = {4,2,7,1,2,9};
```

Find whether a duplicate exists.

Expected:

```text
true
```

---

### Problem 3 — First Non-Repeating

Given:

```text
String s = "aabbcdd";
```

Output:

```text
c
```

---

### Problem 4 — Anagram

Check:

```text
"race"
"care"
```

Expected:

```text
true
```

---

# 34. Level 2

### Problem 5 — Two Sum

```text
nums = [3,2,4]
target = 6
```

Expected:

```text
[1,2]
```

---

### Problem 6 — Maximum Frequency

```text
nums = [1,3,3,2,3,1]
```

Expected:

```text
3
```

---

### Problem 7 — Group Anagrams

```text
["eat","tea","tan","ate","nat","bat"]
```

Group the anagrams.

---

# 35. Level 3

After you are comfortable with the above, learn:

### Problem 8 — Subarray Sum Equals K

Use:

```text
Prefix Sum + HashMap
```

---

### Problem 9 — Longest Subarray With Given Sum

Use:

```text
Prefix Sum + HashMap
```

---

### Problem 10 — Longest Consecutive Sequence

Use:

```text
HashSet
```

Target complexity:

```text
O(n)
```

---

# 36. Interview Cheat Sheet

```text
                    HASHING
                       |
          +------------+------------+
          |                         |
       HashMap                   HashSet
          |                         |
    key → value                 values only
          |                         |
   +------+-------+              |
   |      |       |              |
frequency index mapping       presence
   |      |       |              |
   |      |       |          duplicates
   |      |       |
anagram Two Sum
   |
grouping
```

---

# 37. Quick Decision Guide

When solving a problem, ask:

### 1. Do I need frequency?

```text
YES → HashMap
```

### 2. Do I only need to know whether something exists?

```text
YES → HashSet
```

### 3. Do I need an element's index?

```text
YES → HashMap<Element, Index>
```

### 4. Do I need to find a pair with a target?

```text
YES → Think Two Sum
```

### 5. Do I need to group similar elements?

```text
YES → HashMap<Key, List<Value>>
```

### 6. Do I need subarray sum?

```text
YES → Think Prefix Sum + HashMap
```

---

# 38. Complexity Cheat Sheet

| Problem | Time | Space |
|---|---:|---:|
| Frequency Count | O(n) | O(n) |
| Duplicate Check | O(n) | O(n) |
| Two Sum | O(n) | O(n) |
| Anagram | O(n) | O(k) |
| First Non-Repeating | O(n) | O(k) |
| Group Anagrams | O(n × k log k) | O(n × k) |

Where:

```text
n = number of elements
k = number of distinct characters / average string length
```

---

# 39. What You Should Memorize

Don't memorize every program line-by-line.

Memorize these **five patterns**:

### Pattern 1 — Frequency

```java
freq.put(x, freq.getOrDefault(x, 0) + 1);
```

### Pattern 2 — Presence

```java
if (set.contains(x)) {
    // already seen
}

set.add(x);
```

### Pattern 3 — Two Sum

```java
int needed = target - nums[i];

if (map.containsKey(needed)) {
    // answer
}

map.put(nums[i], i);
```

### Pattern 4 — Character Frequency

```java
for (char ch : s.toCharArray()) {
    freq.put(ch, freq.getOrDefault(ch, 0) + 1);
}
```

### Pattern 5 — Grouping

```java
map.putIfAbsent(key, new ArrayList<>());
map.get(key).add(value);
```

---

# 40. Final Takeaway

For placement DSA, HashMap is not something you should learn as a collection of separate questions.

Learn the **patterns**:

```text
                 HASHING
                    |
       +------------+------------+
       |            |            |
   Frequency     Presence      Mapping
       |            |            |
   HashMap       HashSet      HashMap
       |            |            |
   Anagram       Duplicate    Two Sum
   Counting      Detection    Index
   Grouping                   Prefix Sum
```

Once you recognize these patterns, many seemingly different interview problems become variations of the same idea.

**Priority for your preparation:**

```text
1. HashMap basics
2. Frequency counting
3. HashSet duplicate detection
4. Two Sum
5. Anagram
6. First non-repeating character
7. Group Anagrams
8. Maximum frequency
9. Prefix Sum + HashMap
10. Longest Consecutive Sequence
```

For service-based placement preparation, become very comfortable with **1–8 first**, then move to **9–10**.