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
	- Preorder: Process logic on the current node first before children
	- Inorder: Process logic on the left child first 
	- postorder: Process logic after all traversal 
![[Pasted image 20250309152747.png]]

```python
def preorder_dfs(node):
    if not node:
        return

    print(node.val)
    preorder_dfs(node.left)
    preorder_dfs(node.right)
    return
# Prints: 0,1,3,4,6,2,5

def inorder_dfs(node):
	if not node:
		return

	inorder_dfs(node.left)
	print(node.val)
	inorder_dfs(node.right)
	return
# Prints: 3 1 4 6 0 2 5

def postorder_dfs(node):
	if not node:
		return
	postorder_dfs(node.left)
	postorder_dfs(node.right)
	print(node.val)
	return
# Prints: 3 6 4 1 5 2 0
```
- Time complexity: O(n) where n is the number of nodes
	- O(1) or O(k) work done, so maybe O(n\*k)
- Space complexity :O(n), where it's the largest stack possible (tree with straight line
	- Complete tree is O(logn)

## Breadth First Search
- Traverse all nodes at at given depth before moving on to the next depth
- Use a queue
- DFS is usually quicker because it requires less code
- BFS for handling nodes according to their level
- DFS vs BFS depends on where the node you are looking for
- DFS space is linear to the height of the tree, BFS space is linear to the level with the most nodes
- Time complexity O(n * k), where n is the total number, and the k is the amount of work we do at each node, O(1)

```python
from collections import deque

def print_all_nodes(root):
	queue = deque([root])
	while queue:
		nodes_in_current_level = len(queue)
		# do some logic here for the current level
		for _ in range(nodes_in_current_level):
			node = queue.popleft()
			# do some logic here on the current node
			print(node.val)
			# put the next level onto the queue
			if node.left:
				queue.append(node.left)
			if node.right:
				queue.append(node.right)
	
```

### Binary Search Tree
- Left child is less than root
- Right child is greater than root
- Inorder DFS traversal left before right gets nodes in sorted order

### Graphs
- Inputs are explicity graphs
- First Input Format: Array of Edges
	- Input: 2D Array
	- [1, 2], [3,1], [1, 4]
- Preprocess the input to easily find all neighbors of any given node

#### Array of Edges
```python
from collections import defaultdict

def build_graph(edges: List[List[int]]):
	graph = defaultdict(list)
	for x, y in edges:
		graph[x].append[y]
		# For undirected
		# graph[y].append[x]
	return graph
```

- Second Input Format: Adjacency list
	- Input: 2D Array
	- nodes will be numbered from 0 to n - 1
	- `graph[i]` will list all outoing edges from the ith node
	- All nieghboors at node 6 is `graph[6]`
- Third input format: adjacency matrix
	- Input: 2D matrix of size n x n
	- nodes will be numbered from 0 to n - 1
	- If `graph[i][j] = 1`, means there is an outgoing edge from node i to node j	
```python
from collections import defaultdict

def build_graph(matrix):
	graph = defaultdict(list)
	for i in matrix:
		for j in matrix[x]:
			if matrix[i][j] == 1:
				graph[i].append[j]
				# Undirected, j = 1
	return graph

```
- Last Input: Matrix
	- Describes a story
	- Ex: Each square will represent something, and the squares will be connected in some way. For example, "Each square of the matrix is a village. Villages trade with their neighboring villages, which are the villages directly above, to the left, to the right, or below them."
	- In this case, each square `(row, col)` of a matrix is a node, and the neighboors are 
	- `(row + 1, col), (row - 1, col), (row, col - 1), (row, col + 1) if in bound`

- No obvious starting point
- Add node to seen before traversing (it can be a set)

### Graphs - DFS
```
Example 1: 547. Number of Provinces

There are n cities. A province is a group of directly or indirectly connected cities and no other cities outside of the group. You are given an n x n matrix isConnected where isConnected[i][j] = isConnected[j][i] = 1 if the ith city and the jth city are directly connected, and isConnected[i][j] = 0 otherwise. Return the total number of provinces.

If you're a beginner, we recommend clicking on the problem link and having it open in another tab for all problems in this article so that you can see the example test cases and any images associated with them. You should also be familiar with graph terminology like "connected components". Please review the terminology in the article titled "Graphs" or have it open in another tab if you're not yet familiar with it.
```

- Time complexity O(n + e), where n is the number of nodes and e is the number of edges
- Making adjaceny matrix is O(n^2)
- Space complexity: O(n + e)

### Graphs - BFS
- bruh

