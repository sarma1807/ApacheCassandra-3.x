#### Bulk Load Data into Apache Cassandra using Cassandra Query Language

<hr>

##### Average daily temperature data for major US cities is published by University of Dayton.

http://academic.udayton.edu/kissock/http/Weather/default.htm

<hr>

<b> "usa_daily_avg_temps.csv.gz.tar" </b> contains a subset of data (1995 to 2015) published by University of Dayton (slightly re-formatted).

<b> "usa_daily_avg_temps_sample.csv" </b> contains sample data.

<hr>

### Create Cassandra Keyspace :

CREATE KEYSPACE cassdemo WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 3} ;

or

CREATE KEYSPACE cassdemo WITH replication = {'class':'NetworkTopologyStrategy', 'DC1':3, 'DC2':2} ; <br>

<hr>

### Create Cassandra Table :

CREATE TABLE cassdemo.usa_daily_avg_temps <br>
( <br>
  state text, city text, <br>
  year smallint, month tinyint, day tinyint, <br>
  avgtemp decimal, <br>
  PRIMARY KEY ((state, city), year, month, day) <br>
) WITH CLUSTERING ORDER BY (year DESC, month ASC, day ASC) ; <br><br>

<hr>

### Bulk Load Data into Apache Cassandra using Cassandra Query Language shell (cqlsh) :

COPY cassdemo.usa_daily_avg_temps (state, city, month, day, year, avgtemp) <br>
FROM 'usa_daily_avg_temps.csv' <br>
WITH DELIMITER=',' AND HEADER=true AND NULL='-99' ; <br><br>

<hr>
