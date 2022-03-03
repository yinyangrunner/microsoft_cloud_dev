# Storage abstractions #

## Check your knowledge ##

1. Applications can interact with storage devices using the following abstractions:

__Block devices, file systems, and databases__
_Correct! Applications can interact with storage devices using any of the given abstractions._


# Distributed file systems #

## Check your knowledge ##

1. The Hadoop Distributed File System (HDFS) allows for files to be created only once in its namespace. 
A file, once written, may not be updated or appended to. What file-sharing semantics does HDFS follow?

__Immutable semantics__
_Correct! Since file updates are not a valid operation in HDFS, the file system is immutable._

2. Dropbox is a cloud service that allows users to store and share files on the cloud. Users can install a client application that automatically 
syncs files from the user's local file system to the cloud. When a shared file is opened for writing, Dropbox waits for the application to close 
the file before committing the changes to the cloud. Files can be updated by any client. What file-sharing semantics does Dropbox follow?

__Session semantics__
_Correct! Since updates to a file are propagated only after the file is closed in the client, Dropbox follows session semantics to share files._

# Database design: Schema and scalability #

## Check your knowledge ##

1. Suppose you're designing a storage system for an application that extracts tables from webpages. 
The application plans to assign a unique identifier for each table and then store the table in the database in a raw XML-based format. 
What kind of system might be best suited for this type of application?

__Schemaless database (such as a key-value store)__
_Correct! Given the nature of the data stored, key-value stores offer increased flexibility to the application to store arbitrary data indexed by key._

2. An airline reservation system uses a database to keep track of passengers, airlines, and flights. 
The system is used to book passengers on flights and retrieve the information regarding passengers that have an existing booking on a flight.
What kind of database is most likely in use to power this system?

__OLTP__
_That's correct. This is an example of a transaction processing system. Booking flights and retrieving reservations are simple transactions that affect only a few rows of the database per query.

3. A travel application analyzes flight trends by ingesting worldwide passenger data to provide tourist trends for travel agents and international tour operators. 
What kind of underlying database system is this application most likely to use?
 
__OLAP__
_Correct! This application may have to perform complex queries on the given dataset that may span multiple rows and tables. This is an example of an OLAP system._

# Database design: Consistency and the CAP theorem #

## Check your knowledge ##

1. Suppose a customer of a bank transfers $1,000 into another customer's account and obtains a successful transaction message. 
Five minutes later, the second customer checks their account online and doesn't see the transaction listed. 
Which of the ACID properties was most clearly violated in the case of this transaction?

__The durability of the transaction__
_Correct! The effects of the transaction are expected to persist in the database after the transaction is committed, but the account fails to show so. Hence, there is a violation of the durability property of the transaction.
1 out of 1 questions is incorrect. Please correct question 1._

# Relational databases #
## Check your knowledge ## 
1. A monolithic (single node) RDBMS server is used to deploy a database. Assuming that the database is always reachable and is ACID compliant, 
which of the CAP theorem constraints is satisfied by this server?

__CA__
_Correct! A monolithic server can be consistent and available but is not partition-tolerant, since there is only a single node._

3. Given a system that uses sharding to distribute data among multiple nodes in an RDBMS cluster, which of the following queries will require 
distributed concurrency control (using 2PC or similar mechanisms) to execute safely?

__A query that calculates an aggregate value across all rows of a table and writes that value across all the rows of a table__
_Correct! When a transaction affects multiple rows of a given table, it is likely that it will operate over multiple shards. In this case, distributed concurrency control is required to ensure that the transaction executes safely._


# NewSQL databases #
## Check your knowledge ## 

1. What are the primary tradeoffs in most NoSQL databases?

__Strong consistency is traded for performance and scalability, and consistency is traded for availability and partition tolerance__
_Correct! The primary tradeoff is with consistency. Most NoSQL databases trade consistency to ensure availability and partition tolerance. They also trade strong consistency for performance and availability._

2. An online art creation and distribution website allows users to upload artwork and share it with other users. Other users can comment on and, if the uploader allows, remix the artwork submitted by the original artist. The website has become popular and is now evaluating storage options that can scale as the website continually increases in popularity. Given the needs of the website, what type of database would be the best fit to store the users' artwork?

__Document store__
_Correct! A document store might be the best option for this website because the artwork submitted by users can be treated as individual documents._
