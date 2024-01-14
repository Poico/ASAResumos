Graphs are essential structures for modeling relationships, finding applications from computer networks to transportation. This introduction delves into key algorithms for determining the shortest paths between vertices: Dijkstra's, Bellman-Ford, DAG Shortest Paths, and Johnson's with Graph Repesagem. Each tailored for specific scenarios, these algorithms play a crucial role in optimizing network routing and resource allocation. Join us as we unravel the efficiency and applications of these algorithms in navigating graphs and discovering optimal paths.
# Djikstra's 
Dijkstra's Algorithm, stands as a fundamental solution for efficiently finding the shortest paths between nodes in a graph. Noteworthy for its efficacy in scenarios with non-negative edge weights, this algorithm, often referred to as a "greedy" approach, optimizes routes with precision.
![[Pasted image 20240114163618.png]]
We will find the shortest route to all nodes in the graph starting in A

| A | B | C | D | E |
| ---- | ---- | ---- | ---- | ---- |
| 0 | 4 | 2 | inf | inf |
As the C is the shortest we will now explore in C

| A | B | C | D | E |
| ---- | ---- | ---- | ---- | ---- |
| 0 | 3 | 2 | 5 | 6 |
As B is the shortest we will now explore in B

| A | B | C | D | E |
| ---- | ---- | ---- | ---- | ---- |
| 0 | 3 | 2 | 5 | 6 |

As D is now the only to explore let's go to D it will stay the same so let's go E it stays the same too so now the algorithm as ended and the shortest path to any vertice in the graph is in the table.

# Bellman-Ford

The Bellman-Ford Algorithm, is a versatile solution for finding optimal routes within weighted graphs, even in the presence of negative edge weights. Join us as we explore the essence of the Bellman-Ford Algorithm, unraveling its core principles in the realm of path optimization.

![[Pasted image 20240114165036.png]]

In the Bellman-Ford alghorithm we will do V-1 iteration and we will always start in S and update the values that we can see 
So let's start!

Remember this is a for so we iterate A-B-C-D

**Iteration 1**

| S | A | B | C | D | E |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 0 | 10 | 10 | 12 | 9 | 8 |
**Iteration 2**

| S | A | B | C | D | E |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 0 | 5 | 10 | 8 | 9 | 8 |
**Iteration 3**

| S | A | B | C | D | E |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 0 | 5 | 5 | 7 | 9 | 8 |

**Iteration 4**

| S | A | B | C | D | E |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 0 | 5 | 5 | 7 | 9 | 8 |

As the table stays the same with found the best outcome so we can end now and not do all the iterations :)

# DAG Shortest Paths



# Johnson 
Johnson's algorithm is a method employed in graph theory to address the all-pairs shortest path problem within a weighted directed graph. Unlike certain other algorithms that are limited by the presence of negative edge weights, Johnson's algorithm accommodates both positive and negative weights. The algorithm consists of three main steps, involving the transformation of the graph, the application of the Bellman-Ford algorithm, and the subsequent restoration of the original graph. Johnson's algorithm proves to be efficient, particularly for sparse graphs with a moderate number of vertices and edges, offering a solution to find the shortest paths between all pairs of vertices in a comprehensive yet adaptable manner.

### Step 1: Add a New Vertex and Edges

1.1 **Add a new vertex, say s, to the graph.**

1.2 **Connect s to all existing vertices with zero-weight edges.**

### Step 2: Run Bellman-Ford Algorithm

2.1 **Run the Bellman-Ford algorithm starting from the newly added vertex s.**

- This step detects negative weight cycles if they exist.

2.2 **If a negative weight cycle is detected, halt the algorithm.**

- Johnson's algorithm can't handle graphs with negative cycles.

### Step 3: Modify Edge Weights

3.1 **For each edge (u,v) in the original graph:**

- Adjust the weight of the edge using the formula: w′(u,v)=w(u,v)+d[u]−d[v], where d[u] and ]d[v] are the distances found by the Bellman-Ford algorithm.

### Step 4: Remove the Added Vertex

4.1 **Remove the added vertex s and its incident edges from the modified graph.**

### Step 5: Run Dijkstra's Algorithm for Each Vertex

5.1 **Apply Dijkstra's algorithm for each vertex v in the modified graph.**

- Use the adjusted edge weights from step 3.

5.2 **Record the shortest paths and distances from each vertex �u to every other vertex v.**

### Step 6: Restore Original Distances

6.1 **For each pair of vertices u and v:**

- Adjust the distance found in step 5 by reversing the adjustments made in step 3: d′(u,v)=d(u,v)−d[u]+d[v].