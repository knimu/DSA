# LeetCode 1486 - XOR Operation in an Array

## Approach:

* Initialize `ans = 0`.
* Traverse from `i = 0` to `i < n`.
* Generate each element using `start + 2 * i`.
* XOR every generated element with `ans`.
* Return the final answer.

**Idea:** The array is **not** from `start` to `n`. We have to generate each element using the given formula and XOR them.

**Formula:**

```text
nums[i] = start + 2 * i
```

So the generated array is:

```text
start, start + 2, start + 4, ..., start + 2*(n-1)
```

### Example:

**Input:**

```text
n = 5
start = 0
```

Generated array:

```text
0, 2, 4, 6, 8
```

XOR:

```text
0 ^ 2 ^ 4 ^ 6 ^ 8 = 8
```

**Time Complexity:** `O(n)`
We generate and XOR all `n` elements once.

**Space Complexity:** `O(1)`
No extra space is used.

### Code:

```cpp
class Solution {
public:
    int xorOperation(int n, int start) {
        int ans = 0;

        for (int i = 0; i < n; i++) {
            ans ^= (start + 2 * i);
        }

        return ans;
    }
};
```

**Remember:**
**"Generate each element first (`start + 2*i`), then XOR all the elements."**
