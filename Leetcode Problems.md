
```
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
```