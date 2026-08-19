# Assign Cookies

## Greedy Solution

### Approach:

First, I sort both `Student` and `Cookie` arrays.

Then I use two pointers:

* `l` → points to the current student.
* `r` → points to the current cookie.

I try to give the current cookie to the current student.

If:

```text
Cookie[r] >= Student[l]
```

then the cookie is enough to satisfy that student, so I increase `l`.

In both cases, I increase `r` because I have already checked that cookie.

The main idea is:

> Give the smallest possible cookie that can satisfy the student.

This way, I don't waste a bigger cookie on a student who can be satisfied with a smaller one.

At the end, `l` tells me how many students were satisfied.

---

## Code:

```cpp
class Solution {    
public:
    int findMaximumCookieStudents(vector<int>& Student, vector<int>& Cookie) {
        
        int n = Student.size();
        int m = Cookie.size();

        sort(Student.begin(), Student.end());
        sort(Cookie.begin(), Cookie.end());

        int l = 0;
        int r = 0;

        while(l < n && r < m) {

            if(Cookie[r] >= Student[l]) {
                l++;
            }

            r++;
        }

        return l;
    }
};
```

---

## Dry Run

Suppose:

```text
Student = {1, 2, 3}
Cookie  = {1, 1}
```

After sorting:

```text
Student = {1, 2, 3}
Cookie  = {1, 1}
```

Initially:

```text
l = 0
r = 0
```

### Step 1

```text
Student[l] = 1
Cookie[r]  = 1
```

Since:

```text
1 >= 1
```

the student can be satisfied.

So:

```text
l = 1
r = 1
```

### Step 2

Now:

```text
Student[l] = 2
Cookie[r]  = 1
```

Since:

```text
1 < 2
```

this cookie cannot satisfy the student.

So we only move the cookie pointer:

```text
r = 2
```

Now there are no more cookies.

Therefore:

```text
Answer = 1
```

Only **1 student** can be satisfied.

---

## Why Sorting Helps?

Suppose:

```text
Student = {2, 3}
Cookie  = {2, 3}
```

If I give cookie `3` to the student who needs `2`, then I might not have a suitable cookie left for the student who needs `3`.

Instead:

```text
Student 2 → Cookie 2
Student 3 → Cookie 3
```

Both students are satisfied.

So I should always try to use the **smallest cookie possible**.

---

## Time Complexity:

Sorting the two arrays:

```text
O(n log n + m log m)
```

Traversing both arrays using two pointers:

```text
O(n + m)
```

So overall:

```text
O(n log n + m log m)
```

---

## Space Complexity:

We only use two extra variables `l` and `r`.

```text
O(1)
```

---

## What I Learned:

This is a simple **Greedy + Two Pointer** problem.

The important thing I understood here is:

> **Sort both arrays and always try to satisfy the smallest requirement with the smallest possible resource.**

This helps us maximize the number of students that can be satisfied.
