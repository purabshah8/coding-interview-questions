# Recursion Problems

## Climbing Stairs

You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## Approaches

when n < 3, return based on sub-basecase
n = 1 return 1
n = 2 return 2

otherwise, at the kth step, the number of ways to reach the step is the number of ways to reach the prev step plus the step before that.


## Solutions

Fibonacci

Time Complexity O(n)
Space Complexity O(1)

JavaScript

```js
function climbStairs(n) {
    if (n == 1) return 1;
    if (n == 2) return 2;

    let prevStep = 2;
    let secondPrevStep = 1;
    let allWays = 0;
    for (let i=3; i <= n; i++) {
        allWays = secondPrevStep + prevStep;
        secondPrevStep = prevStep;
        prevStep = allWays;
    }
    return allWays;
}
```

Ruby

```ruby
def climb_stairs(n)
    return 1 if n == 1;
    return 2 if n == 2;

    prev_step = 2;
    second_prev_step = 1;
    all_ways = 0;
    (3..n).each do |n|
        all_ways = second_prev_step + prev_step
        second_prev_step = prev_step
        prev_step = all_ways
    end
    all_ways
end
```