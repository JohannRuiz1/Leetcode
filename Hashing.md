### Hash Map
- Unordered data structure that stores key-value pairs
- Add and Remove elements in O(1)
- Update keys and check if keys exist in O(1)
- Disadvantages
	- For smaller input sizes, too much overhead 
	- Resizing a hash table is more expensive than resizing an array
- Constant time operations are only constant relative to the size of the map 
	- Hashing a string requires O(m), where m is the length of the string
- tuple(arr) to make an array a key
- `for key, val in hash_map.items():`
### Sets
- Useful for checking if elements exist (can't have duplicates)
- Add, remove, check all in O(1)
- Can be used for true or false is something exists

### Checking for Existence

Example 3: Given an integer array `nums`, find all the **unique** numbers `x` in `nums` that satisfy the following: `x + 1` is not in `nums`, and `x - 1` is not in `nums`.
```
def unique(self, nums: List[int]):
	ans = []
	nums = set(nums)
	for num in nums:
		if num + 1 not in set and num - 1 not in set:
			ans.append(num)
	return ans
```

### Counting
- Tracking the frequency of things
- Mapping keys to integers

Example 1: You are given a string `s` and an integer `k`. Find the length of the longest substring that contains **at most** `k` distinct characters.

For example, given `s = "eceba"` and `k = 2`, return `3`. The longest substring with at most `2` distinct characters is `"ece"`.
```
from collections import defaultdict

def distinctCharacters(self, s: str, k: int) -> int:
	#counts = {}
	counts = defaultdict(int)

	ans = left  = 0
	for c in s:
		counts[c] += 1
		while len(counts) > k:
			counts[s[left]] -= 1
			if counts[s[left]] == 0:
				del counts[s[left]]
			left += 1
		ans = max(ans, sum(counts.values()))
	return ans
```
### Collections Library

```
from collections import defaultdict

from collections import Counter
nums = [1, 2, 2, 3, 3, 3]
count = Counter(nums)

print(count)

from collections import deque
dq = deque([1,2,3])
dq.append(4)
dq.appendleft(0)
dq.pop()
dq.popleft()

from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(3,4)

print(p.x, p.y)
print(p)
```

### Count the number of subarrays with an "exact" constraint

- The exact constraint looks to count the status of each subarray in accordance to the condition while iterating such that you can count subarrays that meet the condition by moving that subarray
### Subarray Sum Equals K
```
from collections import defaultdict

class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        counts = defaultdict(int)
        counts[0] = 1
        ans = curr = 0

        for num in nums:
            curr += num
            ans += counts[curr - k]
            counts[curr] += 1
    
        return ans
```

### Subarray Exact Odd Numbers
```
from collections import defaultdict

class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        counts = defaultdict(int)
        counts[0] = 1
        ans = curr = 0

        for num in nums:
            curr += num
            ans += counts[curr - k]
            counts[curr] += 1
    
        return ans
```