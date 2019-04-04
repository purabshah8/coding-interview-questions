# Tree Problems

## Problem
Given a binary search tree and a target, return the closest value that exists in the tree. If the target exists, return the target.

## Approach

Traverse the tree using DFS. If the current node equals target, return the value of node. Else add the children to the stack, with the child further from the target first. Keep a variable that has closest value that updates when a closer value is found. After searching the tree return the closest value


## Solution

```ruby
def bst_target(root, target)
    closest_value = root.val
    stack = [root]
    while stack
        node = stack.pop()
        return node.val if node.val == target
        closest_val = node.val if (target - node.val).abs < (target - closest_value).abs
        if node.left and node.right
            left_diff = (target - node.left.val).abs
            right_diff = (target - node.right.val).abs
            if left_diff < right_diff
                stack.push(node.right)
                stack.push(node.left)
            end
        else
            stack.push(node.left) if node.left
            stack.push(node.right) if node.right
        end
    end
    return closest_value
end
```