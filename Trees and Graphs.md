- Vertices: Nodes of a graph
- Edges: Pointers that connect them 
- 
### Binary Trees
- Start of a tree is the root
- Two children
- Depth of a node is how far it is from the root node
	- The depth of the root is 0
	- Every children has depth = parentsDepth + 1
- Subtree of a tree is a node and all its descendents

```python
class TreeNode:
	def __init__(self, val: int, left: TreeNode, right: TreeNode):
		self.val = val
		self.left = left
		self.right = right
	
```

### Main Tree Logic
- Handle base cases, usually an empty tree
- Do some logic for the current node
- Recursively call on the current node's children
- Return the answer
## Depth First Search
- Traverse a tree in depth first
- Types of searches
	- Preorder