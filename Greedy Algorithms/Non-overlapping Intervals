
````markdown
# Non-overlapping Intervals

## Greedy Solution

### My Understanding

The goal is to **remove the minimum number of intervals** so that the remaining intervals don't overlap.

Instead of thinking:

> "Which intervals should I remove?"

I think:

> "What is the maximum number of intervals I can keep?"

Then:

```text
Minimum removals = Total intervals - Maximum intervals kept
````

### Approach

First, I sort the intervals by their **end time**.

Why?

If I choose the interval that ends earlier, I leave more space for the next intervals.

So the greedy idea is:

> **Keep the interval that finishes earliest.**

Then I go through the intervals one by one.

I keep track of:

```text
lastEnd = end time of the last interval I kept
count   = number of intervals I kept
```

For every interval:

```text
if current start >= lastEnd
```

then there is no overlap, so I keep it.

Otherwise, I skip it.

At the end:

```text
answer = n - count
```

---

## Code

```cpp
class Solution {
public:

    static bool comparator(const vector<int>& a, const vector<int>& b) {
        return a[1] < b[1];
    }

    int eraseOverlapIntervals(vector<vector<int>>& intervals) {

        int n = intervals.size();

        // Sort by end time
        sort(intervals.begin(), intervals.end(), comparator);

        // Keep the first interval
        int lastEnd = intervals[0][1];
        int count = 1;

        // Check remaining intervals
        for (int i = 1; i < n; i++) {

            // No overlap
            if (intervals[i][0] >= lastEnd) {
                count++;
                lastEnd = intervals[i][1];
            }
        }

        // Total - intervals we can keep
        return n - count;
    }
};
```

---

## Dry Run

Suppose:

```text
intervals = [[1,2], [2,3], [3,4], [1,3]]
```

Sort by end time:

```text
[1,2]
[2,3]
[1,3]
[3,4]
```

Start:

```text
lastEnd = 2
count = 1
```

### `[2,3]`

```text
2 >= 2
```

No overlap.

```text
count = 2
lastEnd = 3
```

### `[1,3]`

```text
1 >= 3 ❌
```

Overlap, so skip it.

### `[3,4]`

```text
3 >= 3
```

No overlap.

```text
count = 3
```

So:

```text
Total intervals = 4
Intervals kept  = 3

Answer = 4 - 3 = 1
```

---

## Why Greedy Works?

If I have:

```text
[1,10]
[2,3]
```

I should keep:

```text
[2,3]
```

because it finishes earlier.

Finishing earlier gives me more space to select other intervals.

So the main idea is:

> **Sort by end time and keep the intervals that finish earliest.**

---

## Pattern I Want to Remember 🧠

When I see:

```text
Intervals
+
Overlapping
+
Minimum removals
```

I should think:

```text
Sort by END time
        ↓
Keep maximum non-overlapping intervals
        ↓
Answer = Total - Kept
```

### Time Complexity

Sorting:

```text
O(n log n)
```

Loop:

```text
O(n)
```

Overall:

```text
O(n log n)
```

### Space Complexity

```text
O(1)
```

(excluding the space used by the sorting algorithm)

---

## What I Learned

This is a **Greedy + Sorting** problem.

The important pattern is:

> **When I want to keep the maximum number of non-overlapping intervals, sort by end time and always choose the interval that finishes earliest.**

```
```
