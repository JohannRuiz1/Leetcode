- Priority queue based on the number (min or max)
- Heap complexity
	- Adding an element: O(log(n))
	- Removing an minimum element in O(log(n))
	- Find the minimum element O(1)
- Or maximum is it's a max heap

```python
from heapq import *

heap = []

heappush(heap, 1)
heappush(heap, 2)

# Check minimum element 
heap[0]

# Pop minimum element
heappop(heap) # 1

len(heap)

# Conver a list to a heap in linear time
nums = [43, 2, 13, 634, 120]
heapify(nums)

# Max heap
negNums = [-num for num in nums]
heapift(negNums)

```