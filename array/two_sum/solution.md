# Two Sum

## Brute Force

```js
function twoSum(nums, target) {
    for (let i = 0; i < nums.length; i++) {
        for(let j = i+1; j < nums.length; j++) {
            if (nums[i] + nums[j] == target)
                return [i,j];
        }
    }
}
```

```ruby
def two_sum(nums, target)
    nums.each_with_index do |num, i|
        (i+1...nums.length).each do |j|
            return [i,j] if (num + nums[j]) == target
        end
    end
end
```

## Two Pass Hash Table

```js
function twoSum(nums, target) {
    let visited = {};
    for (let i = 0; i < nums.length; i++) {
        num = nums[i];
        visited[num] = i;
    }
    for (let i = 0; i < nums.length; i++) {
        complement = target-nums[i]
        if (visited[complement]) {
            return [i, visited[complement]];
        }
    }
}
```

```ruby
def two_sum(nums, target) {
    visited = {}
    nums.each { |num,i| visited[num] = i }
    nums.each_with_index do |num, i|
        if visited[target - num]
            return [i, visited[target - num]]
        end
    end
end
}
```

## One Pass Hash Table

```js
function twoSum(nums, target) {
    let visited = {};
    for (let i = 0; i < nums.length; i++) {
        const num = nums[i]
        if (visited[target - num] !== undefined)
            return [visited[target - num], i];
        else
            visited[num] = i;
    }
}
```

```ruby
def two_sum(nums, target)
    visited = {}
    nums.each_with_index do |num, i|
        if visited[target - num]
            return [visited[target - num], i]
        else
            visited[num] = i
        end
    end
end
```