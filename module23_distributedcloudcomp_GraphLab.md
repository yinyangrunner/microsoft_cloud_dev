
# Data structure and graph flow #
## Check your knowledge ##
1. Complete the following sentences:

Graph-parallel problems assume problems are modeled as ____________.
Computation in GraphLab is represented as ____________.
Data dependencies or communications are represented as ____________.

__graphs, vertices, edges__
_Correct! GraphLab assumes problems are modeled as graphs. Computation is represented as vertices. Data dependencies or communications are represented as edges._

2. What does atom generation entail?

__A graph is partitioned into individual atoms and is self-contained with instructions on how to generate the vertices and edges that belong to that partition.__
_Correct! An atom in GraphLab is written using the journal format, which makes atoms self-contained and easy to manipulate to reflect changes in the graph structure. Thus graphs do not require repartitioning in GraphLab if any changes are made._

3. What does partition generation entail?

__The commands in an atom's journal are played to generate the partition associated with an atom.__
_Correct! The atom is formatted as a journal, which contains the commands to generate a partition._

4. Assume the following graph:

Diagram of graph showing vertex V1 connected to V2, V3, and V6; then vertex V2 connected to V4 and V3 connected to V4 and V5.

Assume that the scope of a vertex 
v
 in this graph is defined as the immediate neighboring vertices of 
v
.
Which vertices have the largest scope?

__V1 and V3__
_Correct! V1 and V3 each have a scope of 3._

5. Assume a graph partitioning strategy simply divided up a graph vertex-wise, and sends individual vertices (along with their neighboring edges and ghost vertices) to individual machines in a cluster. In which of the following cases will this strategy be suboptimal in terms of work distributed among the machines in a cluster?

__Graphs with a heavily skewed distribution of edges to vertices__
_Correct! Such graphs will result in some vertices having a large number of edges, which means the machines assigned to process these vertices will be heavily loaded compared to other machines._



# Architectural model # 
## Check your knowledge ##
1. What kind of system is GraphLab?

__Peer-to-peer__
_Correct! Although GraphLab has a monitoring or master engine, processes in the system do not need the master to communicate and perform computation._

2. What strategy does GraphLab use to schedule vertices?

__Push-based__


# Programming model #
## Check your knowledge ##
For the following graph, under the full consistency model, what's the maximum number of vertices that can read or write data in parallel at any given time?
![image](https://user-images.githubusercontent.com/25982256/156889106-dacf5dfa-088f-4e92-bbc3-f503509d7e99.png)
__2__
_Correct! Under the full consistency model, any vertex that's reading or writing data has an exclusive lock on all incident edges and adjacent vertices. In this graph, V5 and V6 can read and write data in parallel as their scopes will not overlap._


# Computational model #
## Check your knowledge ##
1. Complete the following sentence:

GraphLab allows for vertex functions to be executed _______________.

__both synchronously and asynchronously__
_Correct. GraphLab has different engines that can be used to execute vertex functions either synchronously or asynchronously._

# Fault tolerance #
## Check your knowledge ##

1. What are the distributed checkpointing mechanisms that are used in GraphLab?
__Synchronous and asynchronous__
_Correct! Both synchronous and asynchronous distributed checkpointing mechanisms are available in GraphLab._

2. What's the main difference between synchronous and asynchronous mechanisms for checkpointing in GraphLab?

__Synchronous checkpoints suspend the computation and flush all internal communication messages to capture the local checkpoint at every node. Asynchronous checkpoints can be run in parallel on vertices following edge consistency.__
_Correct! Synchronous checkpoints require computation to be suspended, while asynchronous checkpoints can be run in parallel._

# Comparison of distributed analytics engines #
## Check your knowledge ##
1. Which of the following frameworks is best suited to compute all-pairs shortest paths (APSP) on a weighted, fully connected graph?

__GraphLab__
_Correct! APSP on a fully connected graph should converge symmetrically. A graph-parallel framework like GraphLab might be best suited for this application._


