# Array Problems

## Find Kth Largest Element in Array

Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.


## Solution

```js
function findKthLargest(nums, k) {
    let lo = 0;
    let hi = nums.length - 1;
    let pivot_idx;
    while (true) {
        pivot_idx = partition(nums, lo, hi);
        if (pivot_idx === k-1)
            break;
        if (pivot_idx < k - 1)
            lo = pivot_idx + 1;
        else
            hi = pivot_idx - 1;
    }
    return nums[pivot_idx];
};

function partition(nums, left, right) {
    let pivot = nums[left];
    let r = right;
    let l = left + 1;
    while (l <= r) {
        if (nums[l] < pivot && nums[r] > pivot) {
            [nums[l], nums[r]] = [nums[r], nums[l]];
            l += 1;
            r -= 1;
        }
        if (nums[l] >= pivot)
            l++;
        if (nums[r] <= pivot)
            r--;
    }
    [nums[left], nums[r]] = [nums[r], nums[left]]
    return r;
}
```