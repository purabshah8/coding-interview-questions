# Valid Palindrome

## Clean and Check

The high level idea of this approach is to sanitize the input string and save it in a variable. Then check the sanitized string for equalitywith its reverse and return its result.

Time Complexity: **O(n)**

Space Complexity: **O(n)**

## In-place Check

Create two pointers starting at either end of the string. These pointers will advance to the middle of the string, checking for equality of the lower case version of the characters at each step and skipping over spaces. The function will return false if any equality check fails and returns true once the two pointers go past each other.

Time Complexity: **O(n)**

Space Complexity: **O(1)**