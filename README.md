# Modified_Dijkstra_packet_routing


Authors : Heartlin Karan Machado and
Xun Wang


What we promised in proposal: 

Our goal is to provide a solution for using modified Dijkstra algorithms, which a user would specify the additional requirements for the nodes/routers we should avoid and/or go through to solve common routing problems we faced.

We planned to implement 3 routing algorithms: pure Dijkstra, Dijkstra with must-pass nodes, and Dijkstra with must-not-pass nodes. We successfully delivered them in our project.

 

System Design: 

In our system, we first designed the Graph class which has all the setup and information about vertices, edges, and utility function such as printing path.

Then we implemented the core algorithms/methods in a separate class, Dijkstra.java.

We also implemented a utility class called GraphViz.java, which helps visualize the graphs and paths.

Finally, we designed the main class, which is the entry point of our program. In the main method, we first create and setup the graph, then we can call the three algorithms with appropriate parameters, the result should be shown to users as visualized graphs. There are also information printed in the console, either results or exceptions.

Algorithms:

For the implementation of pure Dijkstra, we followed the textbook way of the classic Dijkstra algorithm.

For the implementation of Dijkstra with must-not-pass nodes, we know what nodes we cannot pass. Therefore, our result will not be affected if we remove those nodes and their adjacent edges from the graph. We then create a new graph without the nodes that must not pass, because we do not want to modify the original graph. Next we run our pure Dijkstra on this newly created graph.

For the implementation of Dijkstra with must-pass nodes, our initial approach was to run a BFS with a greedy principle, but we soon realized this cannot guarantee a shortest path. After some research, we found out this problem doesn’t have a polynomial time solution, so we chose the brute force approach, which is not so bad if the number of nodes need to pass are reasonable.

Since the given list of must-pass nodes are not in order, if there exists such a path passing all those nodes, then the order of passing nodes is determinant. We only need to try all permutations of the node orders, and calculate the path cost of each permutation. The one with least-cost is the result. Now we just need to print the path with start node, and then nodes in the order we just found, and lastly destination node.


How to run the program:

In our program, we provided visualization for helping visualize the graph and results, which requires these maven dependencies:
org.jgrapht:jgrapht-core:1.0.0 
org.jgrapht:jgrapht-ext:1.0.0 
com.github.vlsi.mxgraph:jgraphx:4.0.5

For intellij, after download and open our program, follow these steps to add maven dependencies:
1)Go to File->Project structure->Libraries.
2)Click the '+' button and choose from maven.
3)In the search box type "org.jgrapht" and hit the search button.
4)from the dropdown menu which appears after it finishes search choose org.jgrapht:jgrapht-core:1.0.0
5)Click ok again ok then apply.
6)Repeat the same for the other two dependencies.

After adding required dependencies, navigate to Main.java file. In this file, we provide a sample graph for testing and demo purposes. In the main method, we first initialize the graph, then we can run some or all the algorithms we provided.





We can see that these paths are indeed the correct path with the given constraints.

You can define your own graphs and run these algorithms, make sure to check Graph.java class for how to correctly define the graph..

