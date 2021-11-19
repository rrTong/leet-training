# LeetCode Guide

## Objective

The purpose of this markdown file is to write down a methodology to solving every type of algorithmic coding problems that often appear in coding interviews.

## Table of Contents

- [DFS](https://github.com/rrTong/leet-training#dfs)
- [Dynamic Programming](https://github.com/rrTong/leet-training#dynamic-programming)
- [Tree](https://github.com/rrTong/leet-training#tree)
- [Graph](https://github.com/rrTong/leet-training#graph)
- [Sliding Window](https://github.com/rrTong/leet-training#sliding-window)
- [String](https://github.com/rrTong/leet-training#string)
- [Array](https://github.com/rrTong/leet-training#array)
- [Linked List](https://github.com/rrTong/leet-training#linked-list)
- [Matrix](https://github.com/rrTong/leet-training#matrix)
- [Heap](https://github.com/rrTong/leet-training#heap)
- [Binary](https://github.com/rrTong/leet-training#binary)

## DFS

- hold solution in a struct (i.e. list)
- initialize dfs
- dfs()
  - need to know when to stop searching
  - optional: check for duplicates or wrong answers
  - define which paths to explore

```
graph = {
    'A' : ['B','C'],
    'B' : ['D', 'E'],
    'C' : ['F'],
    'D' : [],
    'E' : ['F'],
    'F' : []
}

visited = set()

def dfs(visited, graph, node):
    if node not in visited:
        visited.add(node)
        for neighbour in graph[node]:
            dfs(visited, graph, neighbour)

dfs(visited, graph, 'A')
```

## Dynamic Programming

- basically DFS + memoization (recursion + caching)
- break down problem (recurrence relation)
  - identify base case f(0), f(1)
  - then implement memoization
- top-down vs bottom-up
  - top-down
    - memoization (caching) + recursion
  - bottom-up
    - tabulation (table => array)
      - store results of subproblems
      - always iteration over array

```
memo = {}
memo[0], memo[1] = 1, 1
if n < 2:
  return 1
else:
  for i in range(2, n+1):
    memo[i] = memo[i-1] + memo[i-2]
  return memo[i]
```

## Tree

### Tree Traversal

```
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key

def printInorder(root):
    if root:
        printInorder(root.left)
        print(root.val),
        printInorder(root.right)
```

## Graph

- adjacency list/matrix for each node's neighbors
  - edges in a list of pairs
  - go through all edges to find which nodes are adjacent
  - hashmap or list of lists
  - for loop to initialize adjacency list
  - for loop to populate adjacency list
  - if undirected, edges are added twice

```
rows, cols = len(grid), len(grid[0])
visited = set()

for r in range(rows):
  for c in range(cols):
    if grid[r][c] == "1" and (r, c) not in visited:
      bfs(r, c)
```

## Sliding Window

- used in iterable data structure (strings, arrays)
  - contiguous substring/subarray
- need left and right pointer
  - right pointer moves forward
    - if condition not satisfied: left pointer moves forward
    - right pointer continues to move until end of string/array

```
while r < len(prices):
  if prices[l] < prices[r]:
    profit = prices[r] - prices[l]
    maxP = max(maxP, profit)
  else:
    l = r
  r += 1
```

```
charSet = set()
l = 0

for r in range((len(s))):
  while s[r] in charSet:
    charSet.remove(s[l])
    l += 1
  charSet.add(s[r])
  res = max(res, r-1 + 1)
return res
```

## String

## Array

- hashmap, sliding window, dp

## Linked List

- singly-linked: point forward
- doubly-linked: point forward and backwards
- reorder: change where `next` ptr points to
- deleting node: modify previous node's `next` ptr to skip

### Dummy Node

- dummy node: new node to point to head
  - lets you access & return head easily

```
dummy = ListNode(0, head)
```

### Runner Node (Two Pointers)

- used to locate specific node, since LLs dont have indices
- walker node (left pointer), runner node (right pointer)
  - walker starts at dummy
  - runner starts at N
  - both move forward at same speed
    - when runner hits `null`, walker will be at N

```
left = dummy
right = head

while right:
  left = left.next
  right = right.next
```

## Matrix

- `[[col] row]`
- `grid[row][col]`
- `row = len(grid)`
- `col = len(grid[0])`

```
grid = [[0 for j in range(4)] for i in range(3)]
[[0, 0, 0, 0],
 [0, 0, 0, 0],
 [0, 0, 0, 0]]

grid[0][1] = 1
[[0, 1, 0, 0],
 [0, 0, 0, 0],
 [0, 0, 0, 0]]

>>> len(grid)
3
>>> len(grid[0])
4
```

## Heap

## Binary

### Left Shift <<

- Equivalent to multiplying a number by 2

```
2 << 3
16
```

- 0000 0010
- 0001 0000

### Right Shift >>

- Equivalent to dividing a number by 2

```
8 >> 2
2
```

- 1000
- 0010

### NOT ~

- Switch every bit

```
~3
-4
```

- 0000 0011
- 1111 1100

### AND &

- return 1 if both bit inputs are 1

```
5&3
1
```

- 0101
- 0011 &
- 0001

### OR |

- return 1 if either bit input is 1

```
5|3
7
```

- 0101
- 0011 |
- 0111

### XOR ^

- exclusive OR
- return 1 if bit inputs 1, 0 OR 0, 1

```
7^5
2
```

- 0111
- 0101 ^
- 0010

## Useful Links

[Blind Top 75 Curated List](https://www.teamblind.com/post/New-Year-Gift---Curated-List-of-Top-100-LeetCode-Questions-to-Save-Your-Time-OaM1orEU)

[NeetCode BLIND-75 Playlist](https://www.youtube.com/playlist?list=PLot-Xpze53ldVwtstag2TL4HQhAnC8ATf)

[Kenny Talks Code](https://www.youtube.com/playlist?list=PLujIAthk_iiO7r03Rl4pUnjFpdHjdjDwy)

[EASY GUIDE TO PERFORM BIT MANIPULATION IN PYTHON](https://www.chubbydeveloper.com/bit-manipulation-python/)
