---
layout: post
title:  "Find a Way Out!"
date:   2025-06-09 16:15:00 +0800
categories: computer-related
---

## The maze, DFS, BFS

*Started learning on 0609,*

The maze problem is a classic example in computer science for exploring pathfinding and search algorithms. It naturally inspires two fundamental graph traversal strategies:

- Depth-First Search (DFS) explores one path as deeply as possible before backtracking. In a maze, it's like always choosing one direction and following it until hiting a dead end, then retracing steps to try another path. It uses a stack-based approach (either implicitly via recursion or explicitly with a stack).

- Breadth-First Search (BFS) explores all immediate neighbors before moving deeper. In a maze, it's like moving level by level, exploring all nearby positions before going further. BFS uses a queue and guarantees finding the shortest path in an unweighted maze.