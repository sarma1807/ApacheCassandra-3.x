Bulk Load Data into Apache Cassandra using Cassandra Query Language

<hr>

Create Cassandra Keyspace :

CREATE KEYSPACE cassdemo WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 3} ;

or

CREATE KEYSPACE cassdemo WITH replication = {'class':'NetworkTopologyStrategy', 'DC1':3, 'DC2':2} ;

<hr>

