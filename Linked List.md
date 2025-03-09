```
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None
    
one = ListNode(1)
two = ListNode(2)
three = ListNode(3)
one.next = two
two.next = three
head = one

print(head.val)
print(head.next.val)
print(head.next.next.val)
```
- Keep reference of head to allow go back
- Add and remove elements at certain position is O(1)*
	- Need to have reference to the node where you want to do the add/remove
- O(n) for adding/removing elements at arbirtrary position
- No random access, O(n) to access an element at a given position 
- Not a fixed size
- More overhead than arrays
- Singly linked: next
- Doubly linked: next and prev
- Sentinel Nodes: head and tail nodes for position, no value


### Fast and Slow Pointers
- Pointers move at different speeds
```
function fn(head: ListNode):
	slow = fast = head
	while fast and fast.next
		// Do something
		slow = slow.next
		fast = fast.next.next
```

Example 1: Given the head of a linked list with an **odd** number of nodes `head`, return the value of the node in the middle.

For example, given a linked list that represents `1 -> 2 -> 3 -> 4 -> 5`, return `3`.
```
O(n) time, O(1) space
def middle_value(self, head: ListNode):
	slow = fast = head
	# fast checks even numbered lists, fast.next checks add numbered list
	while fast and fast.next
		slow = slow.next
		fast = fast.next.next
	return slow.val
```

### Reversing a Linked list

```
def reverse_list(head):
	prev = None
	curr = head
	while curr:
		next_node = curr.next # save next node
		curr.next = prev # reverse the direction of the pointer
		prev = curr # set the current node to prev for the next node
		curr = next_node
	return prev
```