# Jump Game

## Greedy Solution

### Approach:

We are given an array where `nums[i]` tells us the **maximum number of steps** we can jump from index `i`.

We need to check if we can reach the last index.

Instead of trying every possible jump, I keep track of the **farthest index I can currently reach**.

I use:

```text id="8k2mqa"
maxreach
```

which stores the maximum index I can reach so far.

For every index `i`:

First, I check:

```text id="p4v7cd"
if(i > maxreach)
```

If this happens, it means I have reached an index that I cannot even get to.

So I return:

```text id="1x9r6b"
false
```

Otherwise, I update the farthest position:

```text id="m3t8ws"
maxreach = max(maxreach, i + nums[i])
```

Here:

```text id="q6f1ze"
i + nums[i]
```

is the farthest position I can reach from the current index.

If I finish the loop, it means I was able to reach every required index, including the last one.

So I return `true`.

---

## Code:

```cpp id="c8v2na"
class Solution {
public:
    bool canJump(vector<int>& nums) {

        int maxreach = 0;

        for(int i = 0; i < nums.size(); i++) {

            // If current index is not reachable
            if(i > maxreach) {
                return false;
            }

            // Update the farthest position we can reach
            maxreach = max(maxreach, i + nums[i]);
        }

        return true;
    }
};
```

---

## Dry Run

Suppose:

```text id="d7q3lm"
nums = {2, 3, 1, 1, 4}
```

Initially:

```text id="z5k8rp"
maxreach = 0
```

### i = 0

```text id="n2f6ya"
nums[0] = 2
```

From index `0`, we can reach:

```text id="r8m1vc"
0 + 2 = 2
```

So:

```text id="b4w9ks"
maxreach = 2
```

---

### i = 1

Since:

```text id="j6p3xd"
1 <= 2
```

index `1` is reachable.

From index `1`:

```text id="a9c5qm"
1 + nums[1]
= 1 + 3
= 4
```

Update:

```text id="h7v2nb"
maxreach = 4
```

Now we can already reach the last index.

---

### i = 2

```text id="s3k8wf"
2 <= 4
```

So index `2` is reachable.

```text id="m5q1az"
2 + nums[2]
= 2 + 1
= 3
```

`maxreach` is already `4`, so it stays:

```text id="v8d4lp"
maxreach = 4
```

---

### i = 3

```text id="e2r7kc"
3 <= 4
```

Reachable.

```text id="y6n3bx"
3 + nums[3]
= 3 + 1
= 4
```

Still:

```text id="u9f5qa"
maxreach = 4
```

---

### i = 4

```text id="w3m8vz"
4 <= 4
```

The last index is reachable.

The loop finishes, so:

```text id="k7p2ds"
Answer = true
```

---

## Example Where We Cannot Reach the End

Suppose:

```text id="x5q9mn"
nums = {3, 2, 1, 0, 4}
```

Initially:

```text id="r1v6kc"
maxreach = 0
```

At index `0`:

```text id="j8m4za"
0 + 3 = 3
```

So:

```text id="c6p2yw"
maxreach = 3
```

We can reach indexes `0, 1, 2, 3`.

At index `3`:

```text id="n9f5bd"
nums[3] = 0
```

So we cannot move any further.

Now when we reach index `4`:

```text id="q4x7ks"
4 > maxreach
4 > 3
```

Index `4` is not reachable.

Therefore:

```text id="a2v8lm"
Answer = false
```

---

## Why Does This Work?

We don't actually need to know the exact jumps we are going to make.

We only care about:

> **What is the farthest index I can reach so far?**

For every reachable index, I try to extend my range.

For example:

```text id="z8c3wp"
index 0 → can reach 2
index 1 → can reach 4
index 2 → can reach 3
```

The important value is always the maximum:

```text id="m1k6qa"
maxreach = 4
```

So we keep extending `maxreach` whenever possible.

---

## Time Complexity

We only go through the array once.

```text id="f8r2nc"
O(n)
```

---

## Space Complexity

We only use one extra variable:

```text id="p5v9xd"
maxreach
```

So:

```text id="h3k7mb"
O(1)
```

---

## What I Learned

This is a **Greedy** problem.

The main idea I understood here is:

> Instead of checking every possible jump, keep track of the farthest index I can reach.

The important condition is:

```cpp
if(i > maxreach)
    return false;
```

If the current index is beyond `maxreach`, there is no way to reach it.

Otherwise, keep updating:

```cpp
maxreach = max(maxreach, i + nums[i]);
```

### Pattern to Remember

```text
Keep track of the farthest reachable position
                    ↓
          Check if current index is reachable
                    ↓
          Extend the reachable range
                    ↓
          Continue until the end
```
