# Data structure #
## Check your knowledge ##
1. Where is the map intermediate output typically written to?

__Local disk__
_Correct! Map intermediate outputs are written by default to the local disk of the node that the map operation was executed on._

2. Where is the reduce output typically written to?

__Hadoop Distributed File System (HDFS)__
_Correct! Reduce task outputs are written by default to HDFS._

3. What is the default relationship between an HDFS block and an input split in MapReduce?

__1:1__
_Correct! The default relationship between an HDFS block and an input split in MapReduce is 1:1. This allows a map task to execute over an entire HDFS block simultaneously._

4. In a MapReduce job, which statement describes the ratio between map and reduce tasks?

__At least one map task and zero to many reduce tasks__
_Correct! A MapReduce job must have at least one map task. Reduce tasks are optional._

5. Where are key-value pairs typically used in MapReduce?

__All of the above__
_Correct! Key-value pairs are typically used for map inputs, intermediate outputs, and reduce outputs._

6. Key-value pair types have to be identical between which of the following phases?

__None of the above__
_Correct! The key-value pair types need to be identical between the output of the map and the input to the reduce phase._

7. What benefits do combiner functions provide in MapReduce?

__A. and B.__
_Correct! Combiners reduce the amount of data shuffled in the network and hence bring potential performance improvements._

8. A MapReduce job uses a reduce function, which calculates the standard deviation of all the values of a particular key. Can a combiner function be used to potentially optimize the runtime of this job and produce the same output?

__No__
_Correct! A standard deviation calculation is neither an associative and commutative nor a distributive operation, and hence, can't be used._

# Example MapReduce programs #
## Check your knowledge ##
1. For the WordCount example, which combiner can be used to get the correct output?

__We can use a reduce function as a combiner to get the same output__
_Correct! The WordCount reducer simply aggregates all of the values for a key and sums them up. We can simply use the same reducer as a combiner function._

# Computation and architectural models #
## Check your knowledge ##
1. Based on Hadoop's architectural model, how are tasks assigned to slots in TaskTrackers?

__Pull strategy: the TaskTrackers notify the JobTracker of vacant slots and ask for tasks to be allotted to their vacant slots.__
_Correct! TaskTrackers always report their status to the JobTracker, which assigns the individual TaskTrackers with tasks if they are free. This is a pull strategy._

# Job and task scheduling #
## Check your knowledge ##
1. How many levels of scheduling are present in Hadoop MapReduce?

__Two levels__
_Correct! Hadoop has two levels of scheduling. Scheduling is present at the job and task levels._

2. Which of the following statements is not true about the FIFO Scheduler?

__The FIFO Scheduler supports job preemption, whereby running jobs can be preempted to make way for waiting jobs to proceed.__
_Correct! This statement is not true. The FIFO Scheduler cannot be preempted to make way for waiting jobs to proceed._

3. What are the main differences between the Fair Scheduler and the Capacity Scheduler?

__A. and C.__
_Correct!_

4. Which of the following task-scheduling mechanisms is locality aware?

__A. Map task scheduler__
_Correct! Only the map task scheduler is locality aware in Hadoop MapReduce._

5. How are skewed partitions formed in MapReduce?

__When the partitioner doesn't distribute immediate key-value pairs evenly across reduce tasks__
_Correct! Partition skew is usually created by the partitioner itself, which may not distribute the intermediate key-value pairs evenly across reducers._


# Fault tolerance #
## Check your knowledge ##
1. How is data redundancy handled in Hadoop MapReduce?

__Data is made redundant through the underlying file system, HDFS, by using replication.__
_Correct! Data redundancy is achieved through HDFS and is not a function of Hadoop MapReduce._

2. How are tasks replicated in Hadoop MapReduce?

__A. and B.__
_Correct! Tasks are replicated for both straggler tasks and dead tasks._

3. The following is a list of some assumptions that Hadoop implicitly makes in speculative execution:

__B., C., and E.__
_Correct! In a heterogeneous cloud, different TaskTrackers may have different hardware and hence may execute tasks at a different rate. In addition, tasks may progress at a different rate. Hence, tasks with low progress scores are not necessarily stragglers._

4. Here are three assumptions that Hadoop implicitly makes in speculative execution:

__B.__
_Correct! The limited bandwidth may affect the shuffle and reduce stages, thereby affecting the task execution rate of a TaskTracker._


