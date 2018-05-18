# Linked list, Queue and Stack

## Linked List

This is an example of a linked list. It's a node that has a pointer to the next node. You can represent it in a code like this.

``` python
class ListNode(object):
    def __init__(self, val):
        self.val = val
        self.next = None

zero = ListNode(0)
one = ListNode(1)
zero.next = one

NULL -> 0 -> 1 -> NULL
```

Here you can see that `zero` node has `val` of `0` and has the `next` pointer to the `one` node. All of the problems with LinkedList you would have to traverse the list and here's how you do it.

``` python
class ListNode(object):
    def __init__(self, val):
        self.val = val
        self.next = None

zero = ListNode(0)
one = ListNode(1)
zero.next = one


def traverse(root):
    current = root
    while current:
        print(current.val)
        current = current.next

traverse(zero)

# It will print
# 0
# 1
```


## Merge sorted lists

### Problem

### Solution