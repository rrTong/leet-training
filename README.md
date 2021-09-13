# LeetCode Guide

## Objective

The purpose of this markdown file is to write down a methodology to solving every type of algorithmic coding problems that often appear in coding interviews.

## Table of Contents

- [LinkedList](https://github.com/rrTong/leet-training#linked-list)
- [DFS](https://github.com/rrTong/leet-training#dfs)
- [Tree](https://github.com/rrTong/leet-training#tree)
- [Graph](https://github.com/rrTong/leet-training#graph)

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

## Useful Links

[Blind Top 75 Curated List](https://www.teamblind.com/post/New-Year-Gift---Curated-List-of-Top-100-LeetCode-Questions-to-Save-Your-Time-OaM1orEU)
[NeetCode BLIND-75 Playlist](https://www.youtube.com/playlist?list=PLot-Xpze53ldVwtstag2TL4HQhAnC8ATf)
[Kenny Talks Code](https://www.youtube.com/playlist?list=PLujIAthk_iiO7r03Rl4pUnjFpdHjdjDwy)
