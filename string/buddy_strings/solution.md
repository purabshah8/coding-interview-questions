# Buddy Strings

```ruby
def buddy_strings(a, b)
    return false if a.length != b.length
    if a == b
        seen = {}
        a.chars.each do |ch|
            return true if seen[ch]
            seen[ch] = true
        end
        return false
    else
        mismatched_idxs = []
        a.length.times do |i|
            mismatched_idxs.push(i) if a[i] != b[i]
        end
        return false unless mismatched_idxs.length == 2
        i = mismatched_idxs[0]
        j = mismatched_idxs[1]
        return true if a[i] == b[j] and b[i] == a[j]
        return false
    end
end
```

```js
function buddyStrings(a, b) {
    if (a.length != b.length)
        return false;
    else if (a === b) {
        seen = new Set();
        for (let i = 0; i < a.length; i++) {
            if (seen.has(a[i]))
                return true;
            else
                seen.add(a[i]);
        }
        return false;
    } else {
        mismatched_idxs = []
        for (let i = 0; i < a.length; i++) {
            if (a[i] !== b[i])
                mismatched_idxs.push(i);
        }
        if (mismatched_idxs.length === 2) {
            if (a[i] === b[j] and b[i] === a[j])
                return true;
            else
                return false
        } else
            return false;
    }
}
```