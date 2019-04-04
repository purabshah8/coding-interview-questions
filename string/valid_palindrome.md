# String Problems

## Valid Palindrome

Given a string, determine if it is a palindrome, ignoring case and spaces. No special characters will be in the input.

## Approaches

O(n) space
Copy string in reverse and compare with original, converted to lower case

O(1) space
Have a pointer at the start of the string and another pointer at the end of the string. Move both pointers towards middle, ignoring spaces, until left pointer goes past right. When moving pointers, if left and right pointers don't point to the same char, return false. Return true at the end if no mismatches are found.

## Solutions

Time Complexity: O(n)
Space Complexity: O(n)

```ruby
def is_palindrome(s)
    s.reverse.lower == s.lower
end
```

Time Complexity: O(n)
Space Complexity: O(1)

```ruby
def is_palindrome(s)
    l = 0
    r = s.length - 1
    while l <= r
        if s[l] == ' '
            l += 1
        elsif s[r] == ' '
            r -= 1
        else
            return false if s[l].downcase() != s[r].downcase()
            l += 1
            r -= 1
        end
    end
    true
end
```

## Variations

what if special characters were included?
