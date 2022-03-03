# Apache HBase #
## Check your knowledge ##

1. How does Apache HBase tolerate region server failures?

__HBase commit logs are written to HDFS, which replicates it across multiple machines.__

2. An operation on an HBase table modifies 10 rows in sequence to zero out one of the columns. The column previously held the value of 1. Simultaneously, another HBase query retrieves the sum of that column over the same 10 rows through a Scan operation. What will be the result of the scan?

__Anywhere between 0 and 10__
_Correct! Because the modification is atomic, each row would be modified correctly. However, the Scan operation is not atomic and could be affected by the row modifications. We cannot be certain of the scan result, and hence it could be any value between 0 and 10._


# Apache HBase #
## Check your knowledge ##

1. Which topology does Cassandra follow?

__Peer-to-peer topology__

2. Which methods are used to keep data replicas in Cassandra consistent?

__All of the above__
_Correct! Cassandra uses all three methods as mechanisms to keep data replicas consistent._

3. An application is using the ONE consistency model for reads and the ALL consistency model for writes. In this mode, Cassandra will offer the application:

__Strong consistency__
_Correct! Using the W + R > N formula, where W = 1 and R = N, the system is strongly consistent for this application._

4. Which of the following consistency models are offered in Cassandra for read operations?

__ONE, QUORUM, ALL__
Correct!


# Apache HBase #
## Check your knowledge ##

1. Which topology does Cassandra follow?

__Peer-to-peer topology__
