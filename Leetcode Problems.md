## Hashing
``` python
class Solution: 
    def minimumRecolors(self, blocks: str, k: int) -> int:
        # Going through the list to see if it already exists to return 0
        # We can do this as we pass through the string

        # Sounds like a sliding window problem, we need to figure out how to remove
        currB = 0 # Consecutive Black Boxes
        ans = len(blocks) # How many operations I've done
        # We can't end this algorithm early because there might be an answer with less operations at the end of the string
        # One way to exist early if we find a condition where operations is 0

        # 1) Loop through and find number of operations, and then continue looping trying to find ones with less
        currW = 0 # num of Ws in the current window => right - left + 1 - curr black boxes
        left = 0 
        for i in range(len(blocks)):
            if blocks[i] == "B":
                currB += 1  
            else:
                currW += 1
            if currB + currW == k:
                ans = min(ans, currW) # Number of white boxes in the current window
                if ans == 0:
                    return ans
                
                if blocks[left] == "W":
                    currW -= 1
                    left += 1
                else:
                    while blocks[left] == "B":
                        currB -= 1
                        left += 1
                    currW -= 1
                    left += 1   
        return ans  

	# Problem 49
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        # Get the letter equvlianet of each character and store that in a hashmap with a list of index
        # if you encounter that hash, add that index to the list
        # At the end, generate your lists by looping through the values in hashmap
        if len(strs) == 0:
            return [[""]]
        anagrams = defaultdict(list)
        for s in strs:
            #key = "".join(sorted(s))
            anagrams[tuple(sorted(s))].append(s)
        
        return list(anagrams.values())

        # anagrams = {}
        # ans = []
        # index = 0
        # for s in strs:
        #     hashValue = sum([hash(c) for c in s])
        #     if hashValue in anagrams:
        #         ans[anagrams[hashValue]].append(s)
        #     else:
        #         # Store the new value into the hashmap
        #         anagrams[hashValue] = index
        #         # Add a new list to the answer
        #         ans.append([])
        #         ans[index].append(s)
        #         index += 1
        return ans
        
    def minimumCardPickup(self, cards: List[int]) -> int:
        # Find the minimum subarray where the start and end equal eachother
        # Maintain a list of cards we've found with their index, and if 
        # we see a value in it, update the answer to be the difference in indexes
        # cards: card: index
        hashmap = {}
        ans = len(cards) + 1
        for i in range(len(cards)):
            card = cards[i]
            if card in hashmap:
                ans = min(ans, i - hashmap[card] + 1)
            hashmap[card] = i
        
        return ans if ans != len(cards) + 1 else -1

	def maximumSum(self, nums: List[int]) -> int:
        counts = {}
        # key = the digit 
        # value = (index, value)
        ans = -1
        # if we find the same digit, keep the one with the higher value
        for i in range(len(nums)):
            digitSum = self.get_digit_sum(nums[i])
            if digitSum in counts:
                index, value = counts[digitSum]
                ans = max(nums[i] + nums[index], ans)
                if nums[i] > nums[index]:
                    counts[digitSum] = [i, nums[i]]
            else:
                counts[digitSum] = [i, nums[i]]
        
        return ans
        # Need to meet the condition and then we can calculate
    
    # Find better way here
    # O(m) is the amount of digits
    def sumOfDigits(self, num: int) -> int:
        # convert the num to string
        s = str(num)
        # Convert the string to a list of characters
        chars = list(s)
        # Convert each character to a int and calculate sum
        digits = [int(c) for c in chars]
        return sum(digits)

    def get_digit_sum(self, num: int) -> int:
        digit_sum = 0
        while num:
            digit_sum += num % 10
            num //= 10
        
        return digit_sum

	def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        # Is ransomNote a subset of magazine
        # i can just the Counter class and make sure each item in ransomNote is less than or euqal to magazine
        # O(n)
        mag = Counter(magazine)
        note = Counter(ransomNote)
        for letter, count in note.items():
            if letter not in mag or mag[letter] < count:
                return False
        
        return True

    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        stonesCount = Counter(stones)
        ans = 0
        for stone, count in stonesCount.items():
            if stone in jewels:
                ans += count
        return ans
```

### Stacks
``` python
class Solution:
    def isValid(self, s: str) -> bool:
        # if you see a close, then the top element on the stack should be the same
        # if it's not, return false
        stack = []
        for c in s:
            if c == ")":
                if not stack or stack.pop() != "(":
                    return False
            elif c == "}":
                if not stack or stack.pop() != "{":
                    return False
            elif c == "]":
                if not stack or stack.pop() != "[":
                    return False
            else:
                stack.append(c)
        return len(stack) == 0


	def isValid2(self, s: str) -> bool:
		stack = []
		matches = {
			"(": ")",
			"{": "}",
			"[": "]"
		}
		for c in s:
			if c in matches:
				stack.append(c)
			else:
				# stack is empty
				if not stack:
					return False
				# We have a closing bracket
				opening_bracket = stack.pop()
				if matches[opening_bracket] != c:
					return False
		# Ensure the stack is empty
		return not stack
	
	def removeDuplicates(self, s: str) -> str:
        # Brute force is looping through for a match and repeating until there are no more
        # If we append to a stack, once there are duplicate sin the stack, we can remove. What's left in the stack is the answer
        # Convert list into str after
        stack = []

        for c in s:
            if stack and stack[-1] == c:
                # Remove the latest character
                stack.pop()
            else:
                # Add character 
                stack.append(c)
        
        return "".join(stack)

	def simplifyPath(self, path: str) -> str:
        # if I split the string using "/", is that a good first step?
        pathItems = path.split("/")
        # If the item is empty, ignore it
        # If the item is ., ignore it
        # If the item is .., pop the last element
        stack = []
        for item in pathItems:
            if item == "..":
                if stack:
                    stack.pop()
            elif item != "" and item != ".":
                stack.append(item)


        print(stack)
        return "/" + "/".join(stack)
```