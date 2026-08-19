
````markdown
# Merge Intervals

## My Understanding

- The goal is to merge all the overlapping intervals.
- After merging, the final answer should contain only non-overlapping intervals.
- The main idea is to sort the intervals first and then process them from left to right.

---

## Approach

- First, sort all intervals by their **start time**.
- Create an `ans` array to store the merged intervals.
- For every interval, compare it with the last interval present in `ans`.
- If they overlap, merge them.
- If they don't overlap, add the current interval separately.

---

## Why Sort by Start Time?

- Sorting by start time puts the intervals in an order that makes them easier to process.
- After sorting, I only need to compare the current interval with the last merged interval.
- This avoids comparing every interval with every other interval.

---

## How to Check Overlap?

Suppose the last interval in `ans` is:

```text
[lastStart, lastEnd]
````

and the current interval is:

```text
[currentStart, currentEnd]
```

### If:

```text
currentStart <= lastEnd
```

* The intervals overlap.
* So, I need to merge them.

### If:

```text
currentStart > lastEnd
```

* There is no overlap.
* So, I add the current interval separately.

---

## How to Merge?

When two intervals overlap:

* The starting point remains the start of the previous merged interval.
* For the ending point, I take the maximum of both ending points.

```cpp
lastEnd = max(lastEnd, currentEnd);
```

Why `max()`?

* The current interval might end later.
* Or it might be completely inside the previous interval.
* Taking the maximum makes sure the merged interval covers both.

---

## Algorithm

1. Sort intervals by start time.
2. Create an empty `ans` array.
3. Traverse all intervals.
4. If `ans` is empty, add the current interval.
5. Otherwise, compare the current start with the end of the last interval in `ans`.
6. If they overlap, merge them using `max()` for the end.
7. If they don't overlap, add the current interval to `ans`.
8. Return `ans`.

---

## Code

```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {

        // Sort by start time
        sort(intervals.begin(), intervals.end());

        vector<vector<int>> ans;

        for (auto interval : intervals) {

            // No overlap
            if (ans.empty() || ans.back()[1] < interval[0]) {
                ans.push_back(interval);
            }

            // Overlap
            else {
                ans.back()[1] = max(ans.back()[1], interval[1]);
            }
        }

        return ans;
    }
};
```

---

## Important Conditions

### Overlap

```text
currentStart <= lastEnd
```

### No Overlap

```text
currentStart > lastEnd
```

### Merge

```text
newEnd = max(lastEnd, currentEnd)
```

---

## Pattern I Want to Remember 

When I see:

```text
Intervals
+
Merge overlapping intervals
```

I should think:

```text
Sort by START
      ↓
Compare with last interval
      ↓
   Overlap?
   /      \
 YES       NO
  ↓         ↓
Merge      Add
```

So the main pattern is:

> **Sort by start time → compare with last interval → merge or add.**

---

## Difference from Non-overlapping Intervals

### Merge Intervals

* Goal → Merge overlapping intervals.
* Sort by → **Start time**.
* If overlap → Merge.

### Non-overlapping Intervals

* Goal → Remove minimum intervals / keep maximum non-overlapping intervals.
* Sort by → **End time**.
* If overlap → Skip one interval.

---

## Time Complexity

* Sorting takes `O(n log n)`.
* Traversing the intervals takes `O(n)`.
* Overall:

```text
O(n log n)
```

## Space Complexity

```text
O(n)
```

* `ans` stores the merged intervals.

---

## What I Learned

* Merge Intervals is an **Intervals + Sorting** problem.
* Sort by **start time**.
* Compare the current interval with the **last interval in `ans`**.
* If they overlap, update the end using `max()`.
* If they don't overlap, add the interval separately.

### One Line to Remember

> **Sort by start → check with last interval → overlap means merge, otherwise add.**

```
```
