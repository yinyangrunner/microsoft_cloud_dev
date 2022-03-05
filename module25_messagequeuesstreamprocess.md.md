
# Message queues #
## Check your knowledge ##
1. Which of the following is not an advantage of message queues over traditional messaging approaches?

__Message queue systems are simpler to set up and less complex architecturally.__
_Correct! Message queues add complexity to a system's architecture._


# Message queues: Case study #
## Check your knowledge ##
1. How would you organize messages in a Kafka cluster, if you needed them to be processed in order by consumers?
__Messages must be published within a partition in a Kafka topic, as all messages within a partition are guaranteed to be ordered.__
_Correct! Kafka guarantees that messages within a partition are ordered by arrival. Messages across partitions or topics are not guaranteed to be ordered._


# Stream processing systems #
## Check your knowledge ##
1. Which of the following is desirable in stream processing engines?

__Partitioning data for scale__
_Correct! These systems are inherently horizontally scalable as long as the data can be sharded across all workers._


# Streaming architectures: Case study #
## Check your knowledge ##
1. Which of the following provides parallelism in Samza?


# Big data processing architectures #
## Check your knowledge ##
1. Which of the following provides parallelism in Samza?

__Partitioning, by dividing the input data into more pieces, allowing parallel processing by multiple tasks__
_Correct! More partitions enable more parallelism._


# Real-time architectures in practice #
## Check your knowledge ##
1. What is the main difference between the Lambda and Kappa architectures?

__Lambda architectures include a layer for batch processing, while Kappa architectures do not.__
