A path finding project using pygame

1.Overview 
∙ Scope of your project describing different  features implemented 
o	Objective of the project is to be able to generate the most optimal path solution between two given points.
o	We have, 4 Path finding algorithms for the user to choose from, namely A – star, Iterative deepening A* (IDA*), DFA* and modified A*. 
	A – star 
	A* is a graph traversal and path search algorithm, which is often used in many fields of computer science due to its completeness, optimality, and optimal efficiency. One major practical drawback is its O(bd) space complexity, as it stores all generated nodes in memory. Thus, in practical travel-routing systems, it is generally outperformed by algorithms which can pre-process the graph to attain better performance, as well as memory-bounded approaches; however, A* is still the best solution in many cases. 
	What A* Search Algorithm does is that at each step it picks the node according to a value-‘f’ which is a parameter equal to the sum of two other parameters – ‘g’ and ‘h’. At each step it picks the node/cell having the lowest ‘f’, and process that node/cell.
	We define ‘g’ and ‘h’ as simply as possible below
	g = the movement cost to move from the starting point to a given square on the grid, following the path generated to get there. 
	h = the estimated movement cost to move from that given square on the grid to the final destination. This is often referred to as the heuristic, which is nothing but a kind of smart guess. We really don’t know the actual distance until we find the path, because all sorts of things can be in the way 


	IDA*
Iterative deepening A* (IDA*) is a graph traversal and path search algorithm that can find the shortest path between a designated start node and any member of a set of goal nodes in a weighted graph. It is a variant of iterative deepening depth-first search that borrows the idea to use a heuristic function to evaluate the remaining cost to get to the goal from the A* search algorithm. Since it is a depth-first search algorithm, its memory usage is lower than in A*, but unlike ordinary iterative deepening search, it concentrates on exploring the most promising nodes and thus does not go to the same depth everywhere in the search tree. Unlike A*, IDA* does not utilize dynamic programming and therefore often ends up exploring the same nodes many times.

	DFA*
DFA* algorithm is an algorithm that uses both the g and the h value that A* applies to measure a cost to visit a node. But unlike A*, to increase the efficiency of the algorithm (path length/ visited nodes), the h value has been drastically increased, to the point where the algorithm behaves like a DFS algorithm, only that unlike DFS which randomly takes any direction, DFA* would take the direction  towards the target. But since it doesn’t check all possible routes, it doesn’t get shortest path possible. How it works:
g and f value is the same as shown in A*
But here f  = (h)^2 + g
Hence as the current node gets close to the end node, the cost is greatly reduced
Let distance between starting and ending node = 5
 
As seen in the above graph, before a node reaches on the 5th node (end node), the cost drastically decreases which makes DFA* to move in one direction


	Modified A-star
Modified A-star, like A* uses the same idea of using g and h for measuring the cost of each node, is similar to DFA* in terms of it’s goal (increasing the efficiency= pathlength/ number of nodes visited). But it the f value is different from  DFA*. It initially spreads from the starting node, and once it is sure in which direction to go in, it behaves similar to DFA*. Comparing it with A* and DFA*, it will have the pathlength greater than or equal to A* while it might be less than DFA*. 
How it works:
g and f value is the same as shown in A*
But here f = g^(h)
Hence as the current node gets close to the end node, the cost first increases and then starts to decreases
Let distance between starting and ending node = 5

 
As seen in the above graph, before a node reaches on the 5th node (end node), the cost first increases drastically, which makes the algorithm to spread, and later the cost decreases due to which the efficiency increases

	Bidirectional Modified A*
In this algorithm, to reduce the chances of going through a longer path in the Modified A* algorithm, from the end node , dijikstra algorithm is executed till certain amount of threshold


  
	
o	We have 3 Maze creation algorithms, DFS, recursive division, modified sidewinder.
	DFS
Frequently implemented with a stack, this approach is one of the simplest ways to generate a maze using a computer. Consider the space for a maze being a large grid of cells (like a large chess board), each cell starting with four walls. Starting from the top left most node, the computer then selects a random neighbouring cell that has not yet been visited. The computer removes the wall between the two cells and marks the new cell as visited, and adds it to the stack to facilitate backtracking. The computer continues this process, with a cell that has no unvisited neighbours being considered a dead-end. When at a dead-end it backtracks through the path until it reaches a cell with an unvisited neighbour, continuing the path generation by visiting this new, unvisited cell (creating a new junction). This process continues until every cell has been visited, causing the computer to backtrack all the way back to the beginning cell. We can be sure every cell is visited.

	Recursive Division
Mazes can be created with recursive division, an algorithm which works as follows: Begin with the maze's space with no walls. Call this a chamber. Divide the chamber with a randomly positioned wall (or multiple walls) where each wall contains a randomly positioned passage opening within it. Then recursively repeat the process on the sub chambers until all chambers are minimum sized. This method results in mazes with long straight walls crossing their space, making it easier to see which areas to avoid.

	Modified Sidewinder
The Sidewinder algorithm starts with an open passage along the entire the top row, and subsequent rows consist of shorter horizontal passages with one connection to the passage above forming multiple trees dropping down from the upper passage. The Sidewinder algorithm is trivial to solve from the bottom up because it has no upward dead ends. Hence we modified the algorithm and removed the upper passage that connects all trees. But since the upper passage is the only path that connects the trees, we randomly make passages from the branches of the trees to other trees. Due to this, there might be chances that one entire tree may be isolated from other trees

o	We allow the user to create a start node(pink) and end node(red), and the walls(black) to barrier the path between the nodes. If the user want’s they can simply generate a maze by clicking on the options, instead of creating one. 
o	If the user wants to use increase/decrease the size of the grid, they can do so by clicking on the +/- button. They can also clear the screen if they would like to.
o	If ever the path is not found a ‘Path Not Found’ Message is displayed in the dialog box.
o	There is special visualization for the path finding with multicolour display as the path progresses.

2.Description about Python Packages used 
•	Pygame is a free and open-source cross-platform library for the development of multimedia applications like video games using Python. It uses the Simple Direct Media Layer library and several other popular libraries to abstract the most common functions, making writing these programs a more intuitive task. Pygame is suitable to create client-side applications that can be potentially wrapped in a standalone executable. Some basic commands :
import pygame - This provides access to the pygame framework and imports all functions of pygame.
pygame.init() - This is used to initialize all the required module of the pygame.
pygame.display.set_mode((width, height)) - This is used to display a window of the desired size. The return value is a Surface object which is the object where we will perform graphical operations.
pygame.event.get()- This is used to empty the event queue. If we do not call this, the window messages will start to pile up and, the game will become unresponsive in the opinion of the operating system.
pygame.QUIT - This is used to terminate the event when we click on the close button at the corner of the window.
pygame.display.flip() - Pygame is double-buffered, so this shifts the buffers. It is essential to call this function in order to make any updates that you make on the game screen to make visible.
•	The priority queue is an advanced type of the queue data structure. Instead of dequeuing the oldest element, a priority queue sorts and dequeues elements based on their priorities. Priority queues are used to handle scheduling problems where some tasks are prioritized over others. The queue.PriorityQueue ClassPython provides a built-in implementation of the priority queue data structure. Since the queue.PriorityQueue class needs to maintain the order of its elements, a sorting mechanism is required every time a new element is enqueued. Python solves this by using a binary heap to implement the priority queue.
•	NumPy is a Python library used for working with arrays. It also has functions for working in domain of linear algebra, fourier transform, and matrices.NumPy aims to provide an array object that is up to 50x faster than traditional Python lists. The array object in NumPy is called ndarray, it provides a lot of supporting functions that make working with ndarray very easy.


3.Screenshots of the system

Using Modified A* 

![image](https://user-images.githubusercontent.com/62883997/118373120-c05cd100-b5d2-11eb-9b82-af05950561d1.png)
![image](https://user-images.githubusercontent.com/62883997/118373123-c94da280-b5d2-11eb-9c02-dba21c04d5eb.png)
![image](https://user-images.githubusercontent.com/62883997/118373132-dcf90900-b5d2-11eb-84b3-547dbce8045c.png)
![image](https://user-images.githubusercontent.com/62883997/118373137-e3878080-b5d2-11eb-8938-d4625217bc7e.png)

Modified Sidewinder

![image](https://user-images.githubusercontent.com/62883997/118373142-ea15f800-b5d2-11eb-9600-cd462c8dcc75.png)
![image](https://user-images.githubusercontent.com/62883997/118373145-ee421580-b5d2-11eb-9b96-269f486fd4f4.png)

Using Modified Bidirectional A*

![image](https://user-images.githubusercontent.com/62883997/118373152-f601ba00-b5d2-11eb-8c92-4bb3f9c92cd5.png)

Increasing/Decreasing grid size
 
![image](https://user-images.githubusercontent.com/62883997/118373158-fd28c800-b5d2-11eb-87ec-fdbd20411979.png)
![image](https://user-images.githubusercontent.com/62883997/118373161-02861280-b5d3-11eb-9ea1-c7b78e1e9dd3.png)


DFS MAZE

![image](https://user-images.githubusercontent.com/62883997/118373164-06b23000-b5d3-11eb-9b16-f406aa017fe4.png)

Using DFA*

![image](https://user-images.githubusercontent.com/62883997/118373182-1a5d9680-b5d3-11eb-81ce-4b2d15765c2a.png)
![image](https://user-images.githubusercontent.com/62883997/118373183-1d588700-b5d3-11eb-8875-d6338265332f.png)
 
IF Path for given nodes is not available: 
![image](https://user-images.githubusercontent.com/62883997/118373191-25182b80-b5d3-11eb-8538-6c510f3a0880.png)


