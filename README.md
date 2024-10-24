### quick review: <https://excalidraw.com/#json=yHsjyn_at8jhO5O_-nNez,tKSX3kQ7fyfgVbTr0UYyKg>


# bfs

BFS: for graph traversal
- take graph, start_vertex

- make a visited list or set to keep track of visited nodes
- make a queue list to keep track of the nodes orders

- put the start node in queue

- while the queue is not empty run the following:
- let n = front node of the queue i.e. 1st element in queue
- pop the front node from the queue

- check if n is in visited list or not
- if no then add n into visited list and print n

- let neighbors = neighbors nodes of n 
- for each neighbor of n do:
- if the neighbor is not in visited list add them in queue list so that they we can pop it and visit it

- done


# BFS: for graph traversal
- take graph, start_vertex

- make a visited list or set to keep track of visited nodes
- make a queue list to keep track of the nodes orders

- put the start node in visited
- put the start node in queue

- while the queue is not empty run the following:
- let n = front node of the queue i.e. 1st element in queue
- pop the front node from the queue

- check if n is in visited list or not
- if no then add n into visited list and print n

- let neighbors = neighbors nodes of n 
- for each neighbor of n do:
- if the neighbor is not in visited list add them in queue list so that they we can pop it and visit it
- and add the neighbor in visited list also
- done




# recursive_best-first_search
##  Recursive-Best-First Search (BFS) algorithm to find the optimal path from a given source node to a target node in a graph.

## Theory:
- The Best-First Search algorithm is a heuristic-based search algorithm that explores the graph by always selecting the node that appears to be closest to the target based on the heuristic function (the `H_dist` dictionary in this case). 
- The algorithm continues to explore the graph until it finds the target node or exhausts all possible paths.

## Here's a detailed explanation of the code:
1. ### Imports:

> `from queue import PriorityQueue:` This line imports the `PriorityQueue` class from the `queue` module, which is used to maintain the priority queue during the search.
---
<br>

2. ### Heuristic Distances `(H_dist):`
> This dictionary stores the heuristic distances (estimated costs) for each node in the graph. The heuristic distance is used to guide the search towards the target node.
---
<br>

3. ### Graph Representation `(Graph_nodes):`
> This dictionary represents the graph, where each key is a node, and the value is a list of its neighboring nodes and their corresponding costs.

---
<br>

4. ### Recursive Best-First Search `(recursive_best_first_search):`
This function implements the recursive version of the Best-First Search algorithm.
-  #### `Parameters:`
    * `graph:` The graph representation.
    * `current_node:` The current node being explored.
    * `target:` The target node to be reached.
    * `visited:` A set of visited nodes to avoid revisiting them.
    * `current_cost:` The current cost of the path from the source to the current node.
    * `parent:` A dictionary to keep track of the parent of each node in the path.

---
<br>

6. ### `Base case:` 
> If the current node is the target node, the function reconstructs the optimal path, prints it, and the total cost, and returns True.

----
<br>

7. ### `Recursive case:`
- The function adds the current node to the visited set.
- It retrieves the list of neighbors for the current node from the graph.
- The neighbors are sorted based on the sum of the current cost, the cost to reach the neighbor, and the heuristic distance to the target.
- The function recursively explores each unvisited neighbor, updating the parent dictionary and the total cost.
- If the recursive call returns `True`, the function returns `True` to indicate that the target has been found.
- If the recursive call returns `False`, the function backtracks by removing the neighbor from the parent dictionary.
- The function returns False if the target node is not found.
---
<br>

8. ### `Best-First Search (best_first_search):`
> This function is the entry point for the Best-First Search algorithm.

- #### `Parameters:`
    * `graph:` The graph representation.
    * `source:` The source node.
    * `target:` The target node.
- The function initializes the visited set and the parent dictionary, with the source node as the root.
- It calls the `recursive_best_first_search` function with the initial parameters and starts the search.
---
<br>

6. ### `Execution:`

> - The code calls the `best_first_search function` with the `Graph_nodes` graph, the `source` node `'S'`, and the `target` node `'G'`.

<br>

for more details: <https://zzzcode.ai/python/code-explain?id=c418ff37-1572-416b-8a4d-19993106c1f4>

# calculations:,
 Start state: S
- From 'S' we can go to 'A' and 'g'

- For S -> A:  f(n) => g(n) + h(n)
                   => 1 + 3 
                   => 4
 
- For S -> g: f(n) => g(n) + h(n)
                  => 10 + 0
                  => 10

- We see that the path with less f(n) is S -> A
- So hold S -> g , and let h1 = 10

- From 'A' we can go to 'B' and 'C'
- For S -> A -> B: f(n) = g(n) + h(n)
                       => 3 + 4
                       => 7

- For S -> A -> C: f(n) = g(n) + h(n)
                       => 2 + 2
                       => 4

- By comparing both f(n), we see that the path S -> A -> C has less f(n)
- So, hold S -> A -> B, and let h2 = 7

- From 'C' we can go to 'D' and 'g':
- For S -> A -> C -> D: f(n) = g(n) + h(n)
                            => 5 + 6
                            => 11


- For S -> A -> C -> g: f(n) = g(n) + h(n)
                             => 6 + 0 
                             => 6

- By comparing both f(n), we see that the path  S -> A -> C -> g has less f(n)
- So, hold S -> A -> C -> D, let h3 = 11

- we have reached our final destination node or goal node
- so let x = f(n) for S -> A -> C -> g
- we check whether any holded f(n) is less than x
- therefore,
  
h1 < x
=> 10 < 6 => false

h2 < x
=> 7  < 6 => false

h3 < x
=> 11  < 6 => false

- Therefore, the optimal path is S -> A -> C -> g
             and the path cost is 6
 
