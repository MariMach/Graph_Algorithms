 # Graph Algorithms

# Overview

The task of this assignment is to investigate different algorithms for a few selected graph analysis problems, to evaluate them and finally to choose one for each problem and implement it in a system of your choice. Note that for every step in this task you should explain your choices and decisions. Also your solution should contain the code (and data is possible) that you used for testing.
Problems
1. Strongly Connected Components: Find all strongly connected components in a graph
2. Path Finding: For a given start vertex, find paths to other vertices in a graph
3. Ranking: Compute a ranking for the vertices in a graph

# Objective 1
For each of the problems listed above, investigate different algorithms that solve the problem. Evaluate different properties of the algorithms that might be important for an implementation. Finally select one algorithm that you would implement to solve the problem. Explain your choice. Some aspects that you should consider might be

1. time complexity
2. memory consumption
3. potential for parallelization
4. restrictions
5. application; e.g. for Ranking, on what type of graphs does the algorithm make sense, how can the result be interpreted
6. feel free to find more aspects

# Objective 2
Implement the three algorithms you chose in the first task in a system and/or language of your choice. Explain your design choices. Note that we will evaluate your solution for performance (or potential bottlenecks) and readability of the code.
Some systems you might want to consider are PGX, SPARK, SNAP or GraphLab but you are free to implement your own. Note that this task requires you to actually implement the algorithm – using built-in functions that do the job is not an option.
In case you chose to implement your own system: Of course you do not have to write an entire graph analytics system. The algorithms including the data-structures you want to use are sufficient – but explain your design choices.

# Types of Graphs

# Undirected Graph
  An undirected graph is a graph in which edges have no orientation.
  The edge (u, v) is identical to the edge (v, u).
  Example : The nodes could represent cities and an edge could represent a bidirectional road.
  
# Directed Graph (Digraph)
  A directed graph or digraph is a graph in which edges have orientations.
  For example, The edge (u ,v) is the edge from node u to node v.
  Example : People in Twitter following each other, A person u bought a gift for v. 

# Weighted Graphs 
  Many Graphs can have edges that contain a certain weight to represent an arbitrary value such as cost, distance, quantity, etc ...
 an edge is represented as a triplet (u, v, w) either if it is directed or undirected.
 
 # Special Graphs
  
  # 1. Trees
   Undirected graphs with no cycles, A tree is is a connected graph with N nodes and N-1 Edges.
   Example: In HTML, the Document Object Model (DOM) works as a tree.
   1. Root is the topmost node of the tree
   2. Edge is the link between two nodes
   3. Child is a node that has a parent node
   4. Parent is a node that has an edge to a child node
   5. Leaf is a node that does not have a child node in the tree
   6. Height is the length of the longest path to a leaf
   7. Depth is the length of the path to its root.
 
 # 2. Binary Trees
   A binary tree is a tree data structure in which each node has at the most two children, which are referred to as the left child and the right child.
   
 # 3. Binary Search Trees
  The difference between a binary tree and a binary search tree is binary trees are not ordered while a binary search tree is ordered.

# 4. Rooted tree
  A rooted tree is a tree with a designated root node where every edge either points away from or towards the root node. When edges point away from the root the graph is called an arborescence (out-tree) and anti-arborescence (in-tree) otherwise.
  
# 5. Directed Acyclic Graphs (DAGs)
  DAGs are directed graphs with no cycles.
  These graphs play an importamt role in representing structures with dependencies.
  Several efficient algorithms exist to operates on DAGs.
  - All out-trees are DAGs but not all DAGs are out-trees.
  
# 6. Bipartite Graph
  A bipartite graph is one whose vertices can be split into two independent groups U, V such that every edge connects between U and V.
  Other definitions exist sush as: The graph is two colourable or there is no odd length cycle.
 
# 7. Complete Graph
  A complete graph is one where is a unique edge between every pair of nodes.
  A complete graph with n vertices is denoted as the graph Kn.
  K5 K3,3 are not planar embeddings (Kuratowski's theorem)
  
# Representing Graphs
  
  # 1. Adjacency Matrix
    Adjacency matrix m is a very simple way to represent a graph.
    The idea is that the cell m[i][j] represents the edge weight of going from node i to node j.
    Node that it is often assumed that the edge of going from a node to itself has a cost of zero.
    Cons : 1. Requires O(V^2) space.
           2. Iterating over all edges takes O(v^2) time
    Pros : 1. Space efficient for representing dense graphs.
           2. Edge weight lookup is O(1). ( m[i][j])
           3. Simplest graph representation.
  # 2. Adjacency List
    An adjacency list is a way to represent a graph as a map from nodes to lists of edges.
    Example : Node A -> [(Node : B, cost : 4), (Node : C, cost : 1)]
              Node B -> [(Node : C, cost : 6)]
              Node C -> [(Node : A, cost : 5), (Node : B, cost : 1)]
    Cons : 1. Less space efficient for denser graphs.
           2. Edge weight lookup is O(E)
           3. Slightly more complex graph representation.
    Pros : 1. Space efficient for representing sparse graphs.
           2. Iterating over all edges is efficient
                   
  # 3. Edge List
    An edge list is a way to represent a graph simply as an unordered list of edges. Assume the notation fpr any triplet (u, v, w) means: the cost from node u to node v is w.
    It is seldomly used because of its lack of structure. However, it is conceptually simple and practical in a hanful algorithms.
    Example :[(C,A,4), (A,C,1), (B,C,6), (A,B,4), (C,B,1)]
    Cons : 1. Less space efficient for denser graphs.
           2. Edge weight lookup is O(E)
    Pros : 1. Space efficient for representing sparse graphs.
           2. Iterating over all edges is efficient
           3. Very simple structure
           
# Common Graph Theory Problems
Is the graph directed or undirected?
Are the edges of the graph weighted?
Is the graph I will encounter likely to be sparse or dense with edges?
Should I use an adjacency matrix, adjacency list, an edge list or other structure to reprsent the graph efficiently?
  # 1. The Shortest Path Problem: 
   Given a weighted graph, find the shortest path of edges from node A to node B.
   Algorithms exists to solve this problem like : 
   1. BFS for unweighted graphs (Brute Force Search)
   2. Dijkstra's
   3. Bellman-Ford
   4. Floyd-Warshall 
   5. A*
   6. ... other
  # 2. Connectivity: 
    Is there a path between node A and node B?
    Typical Solution : Use union find data structure or any search algorithm DFS (Depth first search) or BFS (Breath first search).
    
  # 3. Negative Cycles:
     A negative cycle is a cycle with a negative weight.
     Algorithms : Bellman-Ford and Floyd-Warshall
     
  # 4. Strongly Connected Components:
     Strongly Connected Components (SCCs) can be thought of a self-contained cycles within a directed graph where every vertex in a given cycle can reach every other vertex in the same cycle.
     Algorithms: Tarjan's and Kosaraju's algorithm
     
  # 5. Traveling Salesman Problem:
     "Given a list of cities and the distances between each pair of cities what is the shortest possible route that visits each city exactly once and returns to the origin city?". It is an NP-Hard problem.
     Algorithms: Held-Karp, Branch and Bound, ..
     
   # 6. Bridges:
     A bridge is any edge in a graph whose removal increases the number of connected components.
     Bridges are important in graph theory because they often hint at weak points, bottlenecks or vulnerabilities in a graph.
     Algorithms: 
 
   # 7. Articulation points:
     An articulation point is any node in a graph whose removal increases the number of connected components.
     Articulation points are important in graph theory because they often hint at weak points, bottlenecks or vulnerabilities in a graph.
     Algorithms: 
     
     
   # 8. Minimum Spanning Tree (MST):
     A minimum spanning tree (MST) or minimum weight spanning tree is a subset of the edges of a connected, edge-weighted undirected graph that connects all the vertices together, without any cycles and with the minimum possible total edge weight. ... There are quite a few use cases for minimum spanning trees.
     MSTs are seen in many applications including designing a least cost network, circuit design, transportation networks, and ...etc
     Algorithms: Kruskal's, Prim's and Boruvka's algorithm.
    

   # 9. Network flow (max flow):
    Maximum flow problems involve finding a feasible flow through a single-source, single-sink flow network that is maximum.
    Application Example: The edges are roads with cars, flow represents the number of cars the roads can sustain in traffic.
     Algorithms: Ford-Fulkerson, Edmonds-Karp and Dinic's algorithm.


# Depth First Search (DFS):
The depth-first search is the most fundamental search algorithm used to explore the nodes and edges of a graph. It runs with the time complexity of O(V+E) and is often used as a building block in other algorithms. By itself, the DFS isn't all that useful, but when augmented to perform other tasks such as count connected components, determine connectivity, or find bridges/articulation points then DFS shines.
DFS plunges depth-first into a graph without regard for which edge it takes next until it cannot go any further at which point it backtracks and continues.
# Connected Components:
Assign an integer value to each group to be able to distinguish them instead of coloring them.
use dfs and mark all reachable nodes as being part of the same component.
What else DFS can do ??
. Compute a graph's minimum spanning tree.
. Detect and find cycles in a graph 
. Check if a graph is bipartite.
. Find strongly connected components.
. Topologically sort the nodes of a graph.
. Find bridges and articulation points.
. Find augmenting paths in a flow network.
. Generate mazes.

# Breath First Search (BFS):
The breath-first search is another fundamental search algorithm used to explore the nodes and edges of a graph. It runs with the time complexity of O(V+E) and is often used as a building block in other algorithms. The BFS algorithm is particularly useful for one thing: finding the shortest path on unweighted graphs.
A BFS starts at some arbitrary node of a graph and explores the neighbor nodes first, before moving to the next level neighbors. BFS uses a queue data structure to track which node to visit next.

# Dungeon Problem Statement
You are trapped in a 2D dungeon and need to find the quickest way out!
The dungeon is composed of unit cubes that may or may not be filled with rock.
It takes one minute to move one unit north, south, east, west.
You cannot move diagonally and the maze is surrounded by solid rock on all sides.
Is an escape possible? If yes, how long will it take?

       S : Start 
       E : End 
       R : Rock

       S . . R . . .
       . R . . . R .
       . R . . . . .
       . . R R . . .
       R . R E . R .







  
  
  
  
  
  
 
 
 
 
