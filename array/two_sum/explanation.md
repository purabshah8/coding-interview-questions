# Two Sum

## Brute Force

Check every pair of elements in the array 
using 2 nested loops. If at anytime the sum of elements equals target, break out of the loops and return the indices of the elements. Since an exact solution is guaranteed everytime, there, we do not need a statement after the loop ends.

Time Complexity: **O(n<sup>2</sup>)**

Space Compexity: **O(1)**

## Hash Table

### Two-Pass Hash Table

Loop through array, storing the values in a hash. The keys are array elements and the values are their corresponding indices. Then loop through array again, looking for the complement of current element in hash, returning the two indices if a match is found.

### One-Pass Hash Table

Create a hash and check for the complment in the same loop. If the complement is not found, add the current element to the hash.

Time Compexity: **O(n)**

Space Compexity: **O(n)**