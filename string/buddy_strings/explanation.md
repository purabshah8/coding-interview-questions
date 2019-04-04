# Buddy Strings

If the input strings are not of the same length, then the strings cannot be buddies. For all string pairs of equal length, you have to find the indices where the characters of A differ from B. If there are 2 mismatched indices and `A[i] == B[j] and A[j] == B[i]`, you have a buddy string. The only other situation in which you can have buddy strings is if the strings are equal and they contain repeating characters. To check for this edge case you can store the characters of the string in a set and if you encounter a character already in the set, you can return true.

Time Complexity: **O(n)**

Space Complexity: **O(1)**