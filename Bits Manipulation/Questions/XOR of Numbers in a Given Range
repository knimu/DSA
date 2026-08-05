# XOR of Numbers in a Given Range

## Brute Force Solution

### Approach:

* Initialize `ans = 0`.
* Traverse from `l` to `r`.
* XOR every number with `ans`.
* Return the final answer.

**Idea:** Keep XORing all numbers in the given range.

**Time Complexity:** `O(r - l + 1)`
We traverse every number in the range once.

**Space Complexity:** `O(1)`
No extra space is used.

### Code:

```cpp
class Solution{	
public:
    int findRangeXOR(int l, int r){
        int ans = 0;

        for(int i = l; i <= r; i++){
            ans ^= i;
        }

        return ans;
    }
};
```

---

# Optimal Solution

### Approach:

* Create a function `xortillN(n)` to find XOR from `1` to `n`.
* Observe that XOR from `1` to `n` follows a pattern based on `n % 4`.
* XOR of range `[l, r]` can be found using:

  * `XOR(1...r) ^ XOR(1...l-1)`
* Return the result.

**Idea:** Instead of traversing the range, use the XOR pattern to get the answer in constant time.

**Pattern:**

| n % 4 | XOR(1...n) |
| ----- | ---------- |
| 0     | n          |
| 1     | 1          |
| 2     | n + 1      |
| 3     | 0          |

**Time Complexity:** `O(1)`
Only a few calculations are performed.

**Space Complexity:** `O(1)`
No extra space is used.

### Code:

```cpp
class Solution{
private:
    int xortillN(int n){
        if(n % 4 == 1) return 1;
        if(n % 4 == 2) return n + 1;
        if(n % 4 == 3) return 0;
        return n;
    }

public:
    int findRangeXOR(int l, int r){
        return xortillN(l - 1) ^ xortillN(r);
    }
};
```

**Remember:**
**"Range XOR = XOR(1...R) ^ XOR(1...L-1)"**
