Maze Solver with Graph Implementation

Overview

This project implements a maze-solving algorithm using a graph representation of rooms, corridors, and doors. The goal is to find a path from the entrance to the exit of the maze while using a limited number of coins to open doors. The program reads the maze from an input file and outputs a solution if a valid path exists.

The maze is modeled as an undirected graph, where nodes represent rooms, and edges represent corridors or doors. The program can handle complex mazes where the path may be blocked by doors requiring specific numbers of coins to open.

Features

	•	Graph Representation: The maze is stored as a graph with nodes (rooms) and edges (corridors/doors).
	•	Coin Constraints: The algorithm considers the number of available coins while finding a valid path through the maze.
	•	Pathfinding Algorithm: A depth-first search (DFS) is modified to account for doors and available coins, ensuring the path adheres to constraints.
	•	Input Parsing: The maze is read from an input file that describes the grid structure, rooms, corridors, doors, entrance, and exit.

Classes

	1.	GraphNode.java: Represents a node in the graph (a room in the maze).
	•	Methods:
	•	mark(boolean mark) to mark nodes as visited.
	•	isMarked() to check if a node is marked.
	•	getName() to retrieve the name of the node.
	2.	GraphEdge.java: Represents an edge in the graph (either a corridor or a door).
	•	Methods:
	•	firstEndpoint(), secondEndpoint() to access nodes at each end of the edge.
	•	getType() to get the type of the edge (corridor or door).
	•	getLabel() to get the label of the edge.
	3.	Graph.java: Implements the undirected graph, using an adjacency list or matrix.
	•	Methods:
	•	insertEdge(GraphNode u, GraphNode v, int edgeType, String label) to insert edges into the graph.
	•	getNode(int name) to retrieve a node by its name.
	•	incidentEdges(GraphNode u) to get edges incident on a given node.
	•	areAdjacent(GraphNode u, GraphNode v) to check adjacency between nodes.
	4.	Maze.java: Represents the maze and handles its construction from the input file.
	•	Methods:
	•	Maze(String inputFile) to build the maze graph from the input file.
	•	solve() to find a path from the entrance to the exit, returning an iterator with the nodes in the path.

Input File Format

The input file describing the maze should follow this format:

S
A
L
k
RHRHRH· · ·RHR
VWVWVW· · ·VWV
...

	•	S: Scale factor (not used in the algorithm).
	•	A: Width of the maze (number of rooms per row).
	•	L: Length of the maze (number of rooms per column).
	•	k: Number of coins available to open doors.
	•	RHR/VWV: Grid layout where s marks the entrance, x marks the exit, o represents a room, c is a corridor, w is a wall, and numbers 0-9 represent doors that require coins to open.

Example input:

30
4
3
4
s1owo1o
cwcwcwc
o2o3oco
ww4wcwc
ococx3o

Setup and Usage

	1.	Clone the Repository

git clone https://github.com/yourusername/maze-solver.git
cd maze-solver


	2.	Compile the Java Files

javac *.java


	3.	Run the Program

java Solve inputFile

Example:

java Solve maze.txt

Replace maze.txt with the actual path to your maze input file.

How the Algorithm Works

The maze is solved using a modified depth-first search (DFS). The algorithm traverses the graph, attempting to find a path from the entrance to the exit. If a door is encountered, the algorithm checks if there are enough coins to open it. If the algorithm reaches a dead end or runs out of coins, it backtracks and tries another path.

The solution is represented as a list of nodes (rooms) traversed from the entrance to the exit. If no valid path exists, the program will return null.

Testing

	•	TestGraph: Use this class to test the graph implementation.
	•	Solve: Use this class to test the maze-solving algorithm, providing an input file describing the maze.

License

This project is licensed under the MIT License. See the LICENSE file for details.
