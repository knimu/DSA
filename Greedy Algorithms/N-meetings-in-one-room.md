
````markdown
# N Meetings in One Room

## Greedy Solution

### My Understanding

We have only **one meeting room** and many meetings.

The goal is:

> **Attend the maximum number of meetings.**

The main idea is:

> **Choose the meeting that finishes earliest.**

Why?

Because if a meeting finishes early, the room becomes free earlier and we get more chances to attend other meetings.

---

## Approach

First, I store each meeting as:

```text
(start, end)
````

For example:

```text
Start = [1, 3, 0]
End   = [2, 4, 6]
```

becomes:

```text
(1,2)
(3,4)
(0,6)
```

Then I sort the meetings by their **end time**.

After sorting, I keep track of:

```text
lastEnd = when the room becomes free
count   = number of meetings I attended
```

For every meeting:

```text
if current start > lastEnd
```

then I can attend it.

After attending:

```text
count++
lastEnd = current end
```

At the end, `count` is my answer.

---

## Code

```cpp
class Solution {
public:

    static bool comparator(const pair<int,int>& a,
                           const pair<int,int>& b) {
        return a.second < b.second;
    }

    int maxMeetings(vector<int>& start, vector<int>& end) {

        vector<pair<int, int>> meet;

        int n = start.size();

        // Store meetings as (start, end)
        for (int i = 0; i < n; i++) {
            meet.push_back({start[i], end[i]});
        }

        // Sort by end time
        sort(meet.begin(), meet.end(), comparator);

        // Select the first meeting
        int lastEnd = meet[0].second;
        int count = 1;

        // Check remaining meetings
        for (int i = 1; i < n; i++) {

            if (meet[i].first > lastEnd) {
                count++;
                lastEnd = meet[i].second;
            }
        }

        return count;
    }
};
```

---

## Dry Run

Suppose:

```text
Start = [1, 3, 0, 5, 8, 5]
End   = [2, 4, 6, 7, 9, 9]
```

Meetings:

```text
(1,2)
(3,4)
(0,6)
(5,7)
(8,9)
(5,9)
```

After sorting by end time:

```text
(1,2)
(3,4)
(0,6)
(5,7)
(8,9)
(5,9)
```

Start with:

```text
lastEnd = 2
count = 1
```

### `(3,4)`

```text
3 > 2 ✅
```

Take it:

```text
count = 2
lastEnd = 4
```

### `(0,6)`

```text
0 > 4 ❌
```

Skip it.

### `(5,7)`

```text
5 > 4 ✅
```

Take it:

```text
count = 3
lastEnd = 7
```

### `(8,9)`

```text
8 > 7 ✅
```

Take it:

```text
count = 4
```

So the answer is:

```text
4
```

---

## Why Greedy Works?

Suppose I have:

```text
(1,10)
(2,3)
```

If I choose:

```text
(1,10)
```

the room is busy until `10`.

But if I choose:

```text
(2,3)
```

the room is free at `3`.

So choosing the meeting that finishes earlier gives me more opportunities.

That's why I sort by **end time**.

---

## Pattern I Want to Remember 🧠

When I see:

```text
Meetings / Intervals
+
One resource
+
Maximum number of meetings
```

I should think:

```text
Sort by END time
       ↓
Take the earliest finishing meeting
       ↓
Check if current start > lastEnd
       ↓
If yes → take it
       ↓
Update lastEnd
```

The important greedy idea is:

> **Finish early → get more opportunities later.**

---

## Time Complexity

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

## Space Complexity

We create a vector of meetings:

```text
O(n)
```

---

## What I Learned

This is a **Greedy + Sorting** problem.

The pattern I want to remember is:

> **For maximum non-overlapping meetings, sort by end time and always choose the meeting that finishes earliest.**

```
```
