# Distributed graph databases (Strong Points)
Like a fresh-team in distributed graph databases field wondering which databases is better for our project purposes. So, our team (elastic-team) searched for a high-level perspective titan and neo4j may have.

The action points that elastic-team searched for a distributed database, are the following:

- Performance
- Scalability
- Backend Storage System
- Schema
- Indexing
- Search
- Modeling principles
- APIs

...[more]()

The basic differences between Neo4j (before release 3.0) and Titan is scalability. Titan can distribute
the graph across multiple machines by using either Cassandra or Hbase as the storage backend system.

So after a long search on blogs, project sites, stackoverflow and google groups, we found the following advantages in each distributed graph database

The advantages of **Titan** Graph database:

*  Titan stores large graphs by scaling out

*  Titan handles massive write loads

* No single point of failure - High availability. Unlike with Neo4j's High Availability
setup gives redundancy through replication. For example death of the master leads to
temporary service interruption while a new master is elected.

**Neo4j** is more matures distributed graph database with the following features:
* Neo4j uses lucene indexing mechanism that gives more flexible search engine
* Neo4j provides Cypher query language (Cypher is a declarative, SQL-inspired
language for describing patterns in graphs visually using an ascii-art syntax.) for
additional indexing for full text searches.
* Neo4j features Bolt binary protcol for access in the graph. This protocol provides
a new graph type system (Type safety from language -> driver -> protocol -> cypher -> database engine)
* Official drivers for JS, Java, .NET and Python (based Bolt)
* Neo4j features the new Neo4j Browser, which provides web - based access to
graph database (data graph virtualization). Plus Neo$j browser Sync (Cloud Service)
* Neo4j architecture is designed for optimizing fast management, storage, and traversal
of nodes and relationships. An operation known in the relational database world as a join,
whose performance **degrades exponentially with the number of relationships**,
is performed by Neo4j as navigation from one node to another, whose performance is linear.
* Neo4j uses a replicated master-slave cluster setup. It can store hundreds of trillions
of entities for the largest datasets imaginable while being sensitive to compact storage.
Other features for production applications include hot-backups and extensive monitoring.
* A graph records data in nodes and relationships. Both can have properties.
This is sometimes referred to as the "Property Graph Model".
* Neo4j is used without any schema. Optionally, you can introduce it in order to gain
performance or modeling benefits. This allows a way of working where the schema does
not get in your way until you are at a stage where you want to reap the benefits of having one.
(Schema commands can only be applied on the master machine in a Neo4j cluster)
* Neo4j can help keep your data clean. It does so using constraints. Constraints
allow you to specify the rules for what your data should look like.
