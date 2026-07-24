Single Number III :

Better Solution (Using Hash Map) :

Approach:
Create a hash map to store the frequency of each element.
Traverse the array and increase the frequency of every number.
Traverse the hash map.
If an element has frequency 1, add it to the answer array.
Sort the answer array and return it.

Time Complexity: O(n)
One traversal to store frequencies.
One traversal of the hash map.
Sorting the answer array of size 2 takes O(1).
Overall: O(n).

Space Complexity: O(n)
Hash map stores the frequency of all elements.

Code:

class Solution{	
	public:		
		vector<int> singleNumber(vector<int>& nums){
			//your code goes here
            vector<int> ans;
            unordered_map <int,int> mpp;
            for(int i=0;i<nums.size();i++){
                mpp[nums[i]]++;
            }
            for(auto it : mpp){
                if(it.second==1){
                    ans.push_back(it.first);
                }
            }
            sort(ans.begin(),ans.end());
            return ans;
		}
};

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Optimal Solution (Using Bit Manipulation) :

Why do we use the Rightmost Set Bit?

After taking the XOR of all elements, we get:

Unique1 ^ Unique2
The rightmost set bit tells us a position where the two unique numbers are different.
Using this bit, divide all the numbers into two buckets:
Bucket 1: Numbers having this bit set (1).
Bucket 2: Numbers not having this bit set (0).
Duplicate numbers always go into the same bucket, so they cancel out after XOR.
The two unique numbers go into different buckets, so XOR of each bucket gives one unique number.

Approach:

Find the XOR of all elements in the array. This removes all duplicate numbers and gives the XOR of the two unique numbers.
Find the rightmost set bit in the XOR.
Divide the elements into two buckets based on this bit.
XOR all elements in each bucket separately.
Duplicate numbers cancel out, leaving one unique number in each bucket.
Return the two unique numbers in sorted order.

Time Complexity: O(n)
One traversal to find the overall XOR.
One traversal to divide the elements into two buckets.
Overall: O(n).

Space Complexity: O(1)
Only a few variables are used.

Code :

class Solution {
   public:
    vector<int> singleNumber(vector<int>& nums) {
        // your code goes here
        int n = nums.size();
        long XOR = 0;
        for (int i = 0; i < n; i++) {
            XOR = XOR ^ nums[i];
        }
        int rightmost = (XOR & (XOR - 1)) ^ XOR;
        int XOR1 = 0, XOR2 = 0;
        for (int i = 0; i < n; i++) {
            if (nums[i] & rightmost) {
                XOR1 = XOR1 ^ nums[i];
            } else {
                XOR2 = XOR2 ^ nums[i];
            }
        }
        if (XOR1 < XOR2) {
            return {XOR1, XOR2};
        }
        return {XOR2, XOR1};
    }
};


Easy Trick to Remember :

XOR all elements
        ↓
Get (Unique1 ^ Unique2)
        ↓
Find Rightmost Set Bit
        ↓
Divide into Two Buckets
        ↓
XOR Each Bucket
        ↓
Duplicates Cancel
        ↓
Get the Two Unique Numbers
