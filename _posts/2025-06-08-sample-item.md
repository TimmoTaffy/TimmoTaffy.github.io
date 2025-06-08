---
layout: post
title:  "Tree Traversal is O(n) - Don't Overcomplicate It"
date:   2025-06-08 00:00:00 +0000
categories: computer-related
---

In *Data Structures & Algorithms in Python (Goodrich et al)*, the authors present an algorithm for computing the cumulative space usage of a file-system entry. They spend several paragraphs concluding its time complexity is O(n). Let's directly break it down:

```pseudo
DiskUsage(path):
    total = size(path)
    if path is a directory:
        for each child in path:
            total += DiskUsage(child)
    return total
```

We easily observe the general recursive paradigm:

```pseudo
TreeTraversal(node):
    Do constant work at node
    for each child of node:
        TreeTraversal(child)
```

**Key insight:**
1. Each node is visited exactly once.
2. The work done at each node is O(1).
3. Thus, the overall time complexity is **O(n)**, where *n* is the number of nodes.

Don't be confused by the loop inside the recursion. In essence the recursion ensures that every node is processed once and only once, that's it - no hidden multiplicative factor, just a clean, linear pass through the structure.

<br>
> Tree traversal is O(n). Don't overcomplicate it.
