Bulk Load Data into Apache Cassandra using Cassandra Query Language

<hr>

Average daily temperature data for major US cities is published by University of Dayton.

http://academic.udayton.edu/kissock/http/Weather/default.htm

<hr>

"usa_daily_avg_temps.csv.gz.tar" contains a subset of data published by University of Dayton (slightly reformatted).

"usa_daily_avg_temps_sample.csv" contains sample data.

<hr>

Create Cassandra Keyspace :

CREATE KEYSPACE cassdemo WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 3} ;

or

CREATE KEYSPACE cassdemo WITH replication = {'class':'NetworkTopologyStrategy', 'DC1':3, 'DC2':2} ;

<hr>

