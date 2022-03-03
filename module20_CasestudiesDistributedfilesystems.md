# Case study: Hadoop distributed file system (HDFS) #
## Check your knowledge ##

1. What are the advantages of HDFS over local file systems?

__Common namespace for the cluster, streaming file access, support for large files, and high data availability through replication__

2. When does HDFS commit a write to disk?

__When the last replica has finished writing to a disk__

3. What kind of consistency model does HDFS offer?

__Strong consistency__
_Correct! HDFS's immutable semantics, along with its replica commit policy, give it strong consistency guarantees._


# Case study: CEPH file system #
## Check your knowledge ##

1. At its core, Ceph is a:

__Distributed key-value (object) store__
_Correct! The core component of Ceph is RADOS, which is essentially a distributed key-value store._

2. When writing an application that uses Ceph storage cluster, developers are limited to either RADOSGW, RBD or the CephFS APIs.

__False__
_Correct! The librados library allows developers to interact with a Ceph storage cluster at the lowest (object) level._


