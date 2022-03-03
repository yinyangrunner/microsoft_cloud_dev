
# Categories of computer programs #
## Check your knowledge ##

1. A UNIX shell script uses grep and awk to process plain text files, one at a time, in order to extract information. 
This program is run along with others on a UNIX OS. What kind of program is this most likely to be?

__Sequential__
_Correct! The program runs sequentially over each of the text files._

2. A robot receptionist application runs on a Linux OS and has multiple functional modules that run simultaneously to accomplish several tasks, such as speech generation and facial expressions. These functional modules are designed to be independent processes that can share time on a single processor or core. What kind of program is this most likely to be?

__Concurrent__
_Correct! The program utilizes multiple processes that run concurrently._

3. MATLAB includes a toolbox that automatically takes code written in MATLAB and executes it on multicore processors and/or GPUs to speed up computations. What kind of program does this toolbox most likely generate?

__Parallel__
_Correct! The toolkit runs on multicore processors and/or GPUs to execute instructions in parallel._

4. Folding@Home is a large-scale computing project that uses the idle time of volunteers' computers to perform complex, protein-folding simulations over the internet. What kind of program is Folding@Home most likely to be?

__Distributed__
_Correct! Folding@Home runs across multiple computers connected to a network, hence making it a distributed program._

5. Which of the following statements is true in distributed programs?

__Threads that are part of a single process typically have access to the same memory space.__
_Correct! Threads typically have access to the same memory._

# Programming models for clouds #
## Check your knowledge ##

1. A password-recovery program for ZIP archives works by brute-force trial of the entire password keyspace. The program has a parallel mode, which is used on a single computer but requires a multicore processor. What kind of parallelization technique is this program most likely to utilize?

__Shared memory__
_Correct! As a parallel program running on a single machine with a multicore processor, it is most likely to be using a shared-memory model._

2. A more advanced password-recovery program allows the user to set up a computational cluster using multiple machines to further speed up the brute-force search. The machines in the cluster should be connected using some kind of network but do not implement any kind of distributed shared memory (DSM). What kind of parallelization technique is this program most likely to utilize?

__Message passing__
_Correct! Because the computational cluster does not implement DSM, the only other likely option is message passing._

3. What is the main difference between message-passing and shared-memory models?

__Message passing requires explicit messages to be sent between nodes, while the shared-memory model assumes the existence of a shared address space through which all parallel processes of the application can access data. Shared-memory models require explicit synchronization, while message-passing models do not.__

# Types of parallelism #
## Check your knowledge ##

1. Microsoft's Dryad programming model allows users to express a distributed computational task as a directed acyclic graph (DAG) with the vertices representing computational units and the edges representing the communication between the computational units. The computational units can consist of any program or process. What kind of data parallelism model encompasses Dryad?

__Multiple program, multiple data (MPMD)__
_Correct! Dryad allows any program or process to be used as a computational unit. Hence, more than one program is running concurrently on multiple data. This is MPMD._

2. What are the primary goals of a graph-partitioning technique for graph-parallel programs on a distributed system?

__All of the above.__
_Correct! Graph-partitioning techniques aim to optimize program execution on all these fronts._

# Cloud challenges: Scalability #
## Check your knowledge ##

1. Assume a program that runs for 15 hours on a single processor. One-third of the program consists of data access, which is serial, and the remaining two-thirds consists of computation, which can be parallelized ad infinitum. What is the least amount of time in which the program can execute?

__5 hours__
_Correct! Applying Amdahl's Law, this program cannot execute in less than 5 hours, even with an infinite number of parallel processors._


# Cloud challenges: Communication #
## Check your knowledge ##

1. Why does it make sense to colocate highly communicating entities?

__Improvement in performance and reduction of network traffic__
_Correct! Highly communicating entities should ideally be colocating as closely as possible for both reasons._

# Cloud challenges: Synchronization #
## Check your knowledge ##

1. Assume the following function:
transaction (Account source, Account destination, double amount)
{
  Acquire lock on source;
  Acquire lock on destination;
  withdraw(from, amount);
  deposit(to, amount);
  Release lock on destination;
  Release lock on source;
}
Assume that initially accounts A and B both have 100 dollars and the following operations are executed simultaneously, such that both operations acquire a lock on the source account (as indicated in line number 3 in the transaction function) at the same time:

Copy
1 Transaction(A,B,50); and Transaction(B,A,10);
What will be the result?

__The transactions will never finish due to a deadlock.__
_Correct! The simultaneous acquisition of locks on both A and B by two separate transactions will lead to a deadlock because transaction 1 will fail to acquire the second lock on account B, and transaction 2 will fail to acquire the second lock on account A. At least one of them has to release the lock and start over for the transactions to proceed._


# Cloud challenges: Fault tolerance #
## Check your knowledge ##

1. Consider the actions performed by the processes P and Q in the following figure:
Arrows denote the messages that are passed between the processes.
P1 through P5 denote the checkpoints of P.
Q1 through Q3 denote the checkpoints of Q.
Sequence diagram between process P and Q showing several back-and-forth interactions: from Q to P before checkpoint p1 and back to Q, then from P to Q before checkpoint q1 and back to P before checkpoint p2, then from Q to P and back to Q before checkpoint p3 and then checkpoint q2, then from Q to P before checkpoint p4 and back to Q before checkpoint q3, then four more from P to Q before checkpoint p5, then a failure occurs on Q.
What checkpoints at P and Q form a recovery line that processes P and Q can roll back to?

__P3 and Q2__
_Correct! There are no messages sent between P and Q in between checkpoints P3 and Q2. The checkpoint leads to a consistent state from which the system can recover._


# Cloud challenges: Scheduling #
## Check your knowledge ##
1. What are the considerations for an ideal scheduler for distributed programs?

__All of the above__
_Correct!_

2. Why is meeting SLOs a challenge in cloud computing?

__Heterogeneity in cloud resources and task elasticity is an issue__
_Correct! These are both issues that pose challenges in meeting SLOs in cloud computing._
