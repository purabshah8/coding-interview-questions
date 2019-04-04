# Valid Palindrome

## Clean and Check

```ruby
def valid_palindrome(s)
    s = s.split(" ").join("")
    s.reverse.lower == s.lower
end
```

```js
function validPalindrome(str) {
    str = str.split(" ").join("").toLowerCase();
    let str_reverse = "";
    for (let i = str.length-1; i >= 0; i--) {
        str_reverse += str[i];
    }
    return str === str_reverse;
}
```

## In-Place Check

```ruby
def valid_palindrome(s)
    left = 0
    right = s.length - 1
    while left <= right
        if s[left] == ' '
            left += 1
        elsif s[right] == ' '
            right -= 1
        else
            return false if s[left].downcase() != s[right].downcase()
            left += 1
            right -= 1
        end
    end
    true
end
```

```js
function validPalindrome(str) {
    let left = 0;
    let right = str.length - 1;
    while (left < right) {
        if (str[left] === ' ')
            left += 1;
        else if (str[right] === ' ')
            right -= 1;
        else
            if (str[left].toLowerCase() !== str[right].toLowerCase())
                return false;
            left += 1;
            right -= 1;
    }
    return true;
}
```