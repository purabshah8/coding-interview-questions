# Linked List Problems

## Reverse Linked List

Reverse a singly linked list;


## Approach

**Iterative:** Loop through linked list, changing the next attribute to equal the previous node, which should be stored in a variable. Start prev node as NULL.

**Recursive** Assume you have reversed the end of the list, but just have the beginning left. you have to set the next of the next node to be the current one and then set the next of the current to be null.

## Solutions

### Iterative

Ruby

```ruby
def reverseLinkedList(head)
    curr = head
    prev = nil
    while curr
        tmp = curr.next
        prev = curr
        curr = tmp
    end
    return prev
end
```

JavaScript

```js
function reverseLinkedList(head) {
    let curr = head;
    let prev = null;
    while (curr) {
        let tmp = curr.next;
        curr.next = prev;
        prev = curr;
        curr = tmp;
    }
    return prev;
}
```

### Recursive

JavaScript

```js
function reverseLinkedList(head) {
    if (!head || !head.next)
        return head;
    p = reverseLinkedList(head.next);
    head.next.next = head;
    head.next = null;
    return p;
}
```

Ruby

```ruby
def reverse_linked_list(head) {
    return head if head.nil? or head.next.nil?
    prev = reverse_linked_list(head.next)
    head.next.next = head
    head.next = nil;
    return prev
}
```
