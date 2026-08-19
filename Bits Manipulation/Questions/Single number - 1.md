Single number - 1

Brute Force Solution (Using Hash Map) :

Approach:
Create an unordered map to store the frequency of each number.
Traverse the array and increase the count of every element in the map.
Traverse the map and find the element whose frequency is 1.
Return that element because it appears only once.

Time Complexity: O(n)
One traversal to count the frequency of each element.
One traversal of the hash map to find the element with frequency 1.
Overall: O(n)

Space Complexity: O(n)
An unordered map is used to store the frequency of all elements.

Code:

class Solution {
public:
    int singleNumber(vector<int>& nums) {
        unordered_map<int, int> mpp;

        // Count the frequency of each element
        for (int i = 0; i < nums.size(); i++) {
            mpp[nums[i]]++;
        }

        // Find the element that appears only once
        for (auto doo : mpp) {
            if (doo.second == 1) {
                return doo.first;
            }
        }

        return -1;
    }
};


Optimal Solution (Using XOR) :

Approach:

Initialize a variable sol with 0.
Traverse the array one by one.
Perform XOR (^) of sol with each element.
Since the same numbers cancel each other (a ^ a = 0), only the element that appears once remains.
Return sol.

Time Complexity: O(n) 
Traverse the array only once.
Overall: O(n)

Space Complexity: O(1) 
No extra data structure is used.
Only one variable (sol) is used.

Code:

class Solution {    
public:    
    int singleNumber(vector<int>& nums) {
        int sol = 0;

        // Perform XOR with every element
        for (int i = 0; i < nums.size(); i++) {
            sol ^= nums[i];
        }

        return sol;
    }
};

Why XOR Works?
a ^ a = 0 (same numbers cancel each other)
a ^ 0 = a (XOR with 0 gives the same number)
XOR is commutative and associative, so the order doesn't matter.

Example:

nums = [4, 1, 2, 1, 2]

sol = 0
0 ^ 4 = 4
4 ^ 1 = 5
5 ^ 2 = 7
7 ^ 1 = 6
6 ^ 2 = 4

Answer = 4
