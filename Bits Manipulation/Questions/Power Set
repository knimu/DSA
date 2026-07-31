Bit Manipulation Solution :

Approach:
Find the size of the array n.
Total number of subsets is 2ⁿ (1 << n).
Loop from 0 to 2ⁿ - 1.
Treat each number as a binary representation.
If the ith bit is set, include nums[i] in the current subset.
Store every subset in the answer and return it.

Time Complexity: O(n × 2ⁿ)
There are 2ⁿ subsets.
For each subset, we check all n elements.

Space Complexity: O(n × 2ⁿ)
2ⁿ subsets are stored in the answer.

Code:

class Solution {
public:	
    vector<vector<int> > powerSet(vector<int>& nums) {
        int n = nums.size();
        vector<vector<int>> ans;
        int count = (1 << n);

        for(int val = 0; val < count; val++) {
            vector<int> subset;

            for(int i = 0; i < n; i++) {
                if(val & (1 << i)) {
                    subset.push_back(nums[i]);
                }
            }

            ans.push_back(subset);
        }

        return ans;
    }
};



Dry Run

Suppose,

nums = {1, 2, 3}

Here,

n = 3
count = 1 << 3 = 8

So, we need to generate 8 subsets (0 to 7).

val	Binary	Subset
0	000	{ }
1	001	{1}
2	010	{2}
3	011	{1,2}
4	100	{3}
5	101	{1,3}
6	110	{2,3}
7	111	{1,2,3}
Example (val = 5)
val = 5
Binary = 101

Now check every bit:

i = 0 → 101 & 001 = 1 → Include 1
i = 1 → 101 & 010 = 0 → Skip 2
i = 2 → 101 & 100 = 4 → Include 3

So the subset becomes:

{1, 3}

The same process is repeated for every value from 0 to 7, giving all possible subsets.

