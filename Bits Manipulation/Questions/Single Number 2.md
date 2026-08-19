Single Number 2 

Better Solution (Using Hash Map) :

Approach:
Create a hash map to store the frequency of each element.
Traverse the array and increase the count of every number.
Traverse the hash map.
If any element has frequency 1, return that element.
If no such element is found, return -1.

Time Complexity: O(n)
One traversal to store frequencies.
One traversal of the hash map.
Overall: O(n)

Space Complexity: O(n)
Hash map stores the frequency of all elements.

Code:

class Solution {
public:
    // Function to find the single number
    int singleNumber(vector<int>& nums) {

        // Hash map to store frequency
        unordered_map<int, int> mpp;

        // Store frequency of each element
        for(int i = 0; i < nums.size(); i++) {
            mpp[nums[i]]++;
        }

        // Find the element with frequency 1
        for(auto it : mpp) {
            if(it.second == 1) {
                return it.first;
            }
        }

        return -1;
    }
};


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Optimal Solution (Using Bit Manipulation) :

Approach:
Initialize the answer as 0.
Check every bit position from 0 to 31.
For each bit, count how many numbers have that bit set.
If the count is not divisible by 3, then that bit belongs to the single number.
Set that bit in the answer.
After checking all 32 bits, return the answer.

Time Complexity: O(32 × n)
Check all 32 bits.
For every bit, traverse the array once.
Since 32 is constant, overall complexity is O(n).

Space Complexity: O(1)
Only a few variables are used.

Code:

class Solution {
public:
    // Function to find the single number
    int singleNumber(vector<int>& nums) {

        int n = nums.size();
        int ans = 0;

        // Check every bit position
        for(int bitIndex = 0; bitIndex < 32; bitIndex++) {

            int count = 0;

            // Count set bits at current position
            for(int i = 0; i < n; i++) {
                if(nums[i] & (1 << bitIndex)) {
                    count++;
                }
            }

            // Set the bit if count is not divisible by 3
            if(count % 3 != 0) {
                ans |= (1 << bitIndex);
            }
        }

        return ans;
    }
};

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Brute Force Solution (Using Sorting) :

Approach:
Sort the given array so that all identical elements come together.
Traverse the sorted array by checking every group of three elements.
Compare the current element with the previous one.
If they are different, the previous element is the single number.
If no such element is found during traversal, the last element of the sorted array is the single number.

Time Complexity: O(n log n)
Sorting the array takes O(n log n).
Traversing the array takes O(n/3) ≈ O(n).
Overall complexity: O(n log n).

Space Complexity: O(1)
Only a few variables are used (ignoring the sorting algorithm's internal space).

Code :

class Solution {
public:
    int singleNumber(vector<int>& nums) {        
        //your code goes here
        int n=nums.size();
        sort(nums.begin(),nums.end());
        for(int i=1;i<n;i+=3){
            if(nums[i]!=nums[i-1]){
                return nums[i-1];
            }
        }
        return nums[n-1];
    }
};

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

