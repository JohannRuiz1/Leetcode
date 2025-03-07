## Two Pointer
- Start one pointer at the first index `0` and the other point at the last index `input.length - 1`
- Use a while loop until the pointers are equal to each other
- At each iteration of the loop, move the pointers towards each other. This means either increment the pointer that started at the first index, decrement the pointer that started at the last index, or both. Decided what to do it solving the problem

### Palindrome: 
```
def check_if_palindrome(s: str) -> bool:
    left = 0
    right = len(s) - 1

    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1
    
    return True
```

### Two Sums (Sorted):
```
def two_sum(self, nums: List[int], target: int) -> List[int]:
	left = 0
	right = len(nums) - 1
	while left < right:
		curr =. nums[left] + nums[right]
		if(curr == target):
			return [left, right]
		if(curr > target):
			right = right - 1
		else:
			left = left + 1
	return []
```

## Two Sums (Unsorted)
```
def two_sums_unsorted(self, nums: List[int], target: int) -> List[int]:
	left = 0
	right = len(nums) - 1
	complements = {}
	for i in range(len(nums)):
		num = nums[i]
		neededNumber = target - num
		# Is the neededNumber in the dictionary
		if neededNumber in complements:
			return [i, complements[neededNumber]]
	
		complements[num] = i

	return []


```

- Two pointers can also work for iterating between multiple lists

```
class Solution:
	def isSubsequence(self, s: str, t: str) -> bool:
		j = 0
		if len(s) == 0:
			return True
		if len(s) > len(t):	
			return False
		
		for i in range(len(t)):
			if t[i] == s[j]:	
				j = j + 1	
				if len(s) == j:
					return True
		
		return False
```


Example 1: Given an array of positive integers `nums` and an integer `k`, find the length of the longest subarray whose sum is less than or equal to `k`. This is the problem we have been talking about above. We will now formally solve it.
**right - left + 1 is the size of the subarray and also the amount of subararys between indexes**

```
class Solution:
	def function_the_long_way(self, nums: List[int], k: int):
		# curr is the current answer, left is the left index, ans is the answer
		left = curr = ans = 0
		for i in range(len(nums)):
			curr += nums[i]
			while curr > k:
				curr -= nums[left]
				left += 1
			
			ans = max(curr, right - left + 1)
		return ans
	
```

Example 2: You are given a binary string `s` (a string containing only `"0"` and `"1"`). You may choose up to one `"0"` and flip it to a `"1"`. What is the length of the longest substring achievable that contains only `"1"`?

For example, given `s = "1101100111"`, the answer is `5`. If you perform the flip at index `2`, the string becomes `1111100111`.

```
class Solution:
	def binary(self, s: str) -> int:
		ans = left = curr = 0
		for i in range(len(s)):
			if s[i] == "0":
				curr += 1
			while curr > 1:
				if s[left] == "0":
					curr -= 1
				left += 1
			ans = max(ans, right - left + 1)
		return ans
```



Example 3: [713. Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/).

Given an array of positive integers `nums` and an integer `k`, return the number of subarrays where the product of all the elements in the subarray is strictly less than `k`.

For example, given the input `nums = [10, 5, 2, 6], k = 100`, the answer is `8`. The subarrays with products less than `k` are:

`[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]`
3
```
class Solution:
	def lessThanK(self, nums: List[int], k: int) -> int:
		if k <= 1:
            return 0
        
		left = ans = 0
		currProd = 1
		for i in range(len(nums)):
			# Get the current product
			currProd *= nums[right]
			while currProd > k:
				currProd //= nums[left]
				left+=1
			# This is the current amount of subarrays
			ans += i - left + 1
			
		return ans 
```

Example 4: Given an integer array `nums` and an integer `k`, find the sum of the subarray with the largest sum whose length is `k`.
```
class Solution:
	def subarray(self, nums: List[int], k: int) -> int:
		sum = curr = ans = 0
		# Find the window size
		for i in range(k):
			ans += nums[i]
			
		sum = ans
		
		for i in range(k, len(nums)):
			sum -= nums[curr]
			sum += nums[i]
			ans = max(ans, sum)
			curr += 1
		return ans
```

## Prefix Sum 

