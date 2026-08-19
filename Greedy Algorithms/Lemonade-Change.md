# Lemonade Change

## Greedy Solution

### Approach:

We have to give the correct change to every customer.

The lemonade costs `$5`, so:

* If the customer gives `$5`, no change is needed.
* If the customer gives `$10`, we need to give `$5` back.
* If the customer gives `$20`, we need to give `$15` back.

I keep track of how many `$5` and `$10` bills I currently have.

```text id="q6x8rp"
five → number of $5 bills
ten  → number of $10 bills
```

For a `$5` bill:

```text id="8ud8l7"
Just increase five.
```

For a `$10` bill:

We need `$5` as change.

So if I have a `$5`:

```text id="8a6r5v"
five--;
ten++;
```

Otherwise, I return `false`.

For a `$20` bill:

We need `$15` as change.

There are two possible ways:

```text id="7v3a2m"
$10 + $5
```

or

```text id="f5m8dd"
$5 + $5 + $5
```

I prefer using **one `$10` and one `$5` first**.

Why?

Because `$5` bills are more useful for giving change to future customers.

If I use three `$5` bills when I have a `$10`, I might run out of `$5` bills later.

If neither option is possible, I return `false`.

---

## Code:

```cpp id="h7x2mb"
class Solution {    
public:    
    bool lemonadeChange(vector<int>& bills) {

        int five = 0;
        int ten = 0;

        for(int i = 0; i < bills.size(); i++) {

            if(bills[i] == 5) {
                five++;
            }

            else if(bills[i] == 10) {

                if(five > 0) {
                    five--;
                    ten++;
                }
                else {
                    return false;
                }
            }

            else if(bills[i] == 20) {

                // Prefer $10 + $5
                if(five > 0 && ten > 0) {
                    five--;
                    ten--;
                }

                // Otherwise use three $5 bills
                else if(five >= 3) {
                    five -= 3;
                }

                else {
                    return false;
                }
            }
        }

        return true;
    }
};
```

---

## Dry Run

Suppose:

```text id="zq1l6e"
bills = {5, 5, 5, 10, 20}
```

Initially:

```text id="y8f3m0"
five = 0
ten = 0
```

### Bill = 5

No change is needed.

```text id="e9f5q1"
five = 1
ten = 0
```

### Bill = 5

Again, no change is needed.

```text id="m7n2xa"
five = 2
ten = 0
```

### Bill = 5

```text id="c1v4ks"
five = 3
ten = 0
```

### Bill = 10

Need `$5` change.

We have one `$5`, so:

```text id="4gq6pw"
five = 2
ten = 1
```

### Bill = 20

Need `$15` change.

We have both `$10` and `$5`, so use:

```text id="2zj8fn"
$10 + $5
```

Now:

```text id="0x8s7n"
five = 1
ten = 0
```

Everyone received the correct change.

Therefore:

```text id="w3f6kj"
Answer = true
```

---

## Another Example

Suppose:

```text id="3j8r6p"
bills = {5, 5, 10, 10, 20}
```

After the first two `$5` bills:

```text id="4m1c7v"
five = 2
ten = 0
```

First `$10`:

```text id="h2k9qs"
five = 1
ten = 1
```

Second `$10`:

```text id="p8d4zn"
five = 0
ten = 2
```

Now the `$20` customer comes.

We need `$15` change, but:

```text id="s6w2er"
five = 0
```

We cannot make `$15`.

So:

```text id="x9k3lm"
Answer = false
```

---

## Why Do We Prefer `$10 + $5` for `$20`?

This is the main greedy idea in this problem.

Suppose:

```text id="f4t7qa"
five = 2
ten = 1
```

A `$20` bill needs `$15`.

We could use:

```text id="j2m8vc"
$5 + $5 + $5
```

but we only have two `$5` bills.

Instead, we can use:

```text id="r5n1bx"
$10 + $5
```

So whenever possible, we should use `$10 + $5`.

The reason is that **`$5` bills are more flexible**. They can be used to give change for both `$10` and `$20` bills.

---

## Time Complexity

We go through the `bills` array only once.

```text id="v7p2dk"
O(n)
```

where `n` is the number of customers.

---

## Space Complexity

We only store two variables:

```text id="q3m8hf"
five
ten
```

So:

```text id="k5r1zs"
O(1)
```

---

## What I Learned

This is a **Greedy** problem.

The main thing I understood here is:

> For every `$20` bill, try to give `$10 + $5` first, because `$5` bills are more useful for future customers.

So the general idea is:

```text id="n8c4yw"
$5  → save it
$10 → give one $5 as change
$20 → give $10 + $5 if possible
```

If at any point I cannot provide the required change, I return `false`.
