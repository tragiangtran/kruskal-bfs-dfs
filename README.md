# Minimum Spanning Tree (MST) & Graph Traversal (Kruskal, BFS, DFS)

A Python implementation of **Kruskal's Algorithm** for finding the Minimum Spanning Tree (MST) on undirected, weighted graphs, featuring cycle detection via **Breadth-First Search (BFS)** or **Depth-First Search (DFS)**.

---

## Overview
Finding a **Minimum Spanning Tree (MST)** connects all vertices in a weighted graph with the minimum total edge weight and no cycles.

This project demonstrates:
1. **Breadth-First Search (BFS):** Layer-by-layer traversal using a FIFO queue (collections.deque) to determine reachability and predecessor paths.
2. **Depth-First Search (DFS):** Deep-first path exploration implemented iteratively with an explicit LIFO stack.
3. **Kruskal's Algorithm:** A greedy approach that builds the MST edge by edge, leveraging **BFS** to detect connectivity and avoid premature cycle formation.

---

## Algorithmic Logic

### 1. Kruskal's MST Construction
- **Greedy Selection:** Edges are sorted in ascending order of their weights.
- **Cycle Detection via:** 
  Before adding an edge $(u, v)$ with weight $w$ to the MST:
  - Run BFS on the current tree edges.
  - If node $v$ has **no predecessor**, it implies $u$ and $v$ belong to separate components $\rightarrow$ adding $(u, v)$ is **safe and cycle-free**.
  - If a path between $u$ and $v$ already exists, the edge is discarded to prevent cycle formation.
- **Termination:** The algorithm terminates as soon as $\vert{}V\vert{} - 1$ edges are collected.

### 2. Traversal Mechanics
- **BFS:** Uses `deque.popleft()` and a boolean `visited` array to guarantee shortest-hop predecessor tracking.
- **DFS:** Uses an explicit `stack` of `(current_node, parent_node)` pairs to track graph branch traversal without recursion limits.
