
### Stacks
- LIFO
- String questions involving stacks are popular
```python
stack = []
stack.append(1)
stack.pop()
stack[-1]
```

### Queues
- FIFO
- Used in BFS 
```python
from collections import deque
queue = deque()

queue = deque([1,2,3])

queue.append(4)
queue.append(5)

queue.popleft() # 1
queue.popleft() # 2

queue.popright() # 5

queue[0] # 3

len(queue)
```


### Monotonics 
- Come back to monotonic