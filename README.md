# Neo4j_vs_Titan
A short markable repository which has as main role to describe the difference between the graph databases

# Distrinuted graph databases (performing differences)
Like a fresh-men in distributed graph databases field, we are wondering which databases is
better in a high-level perspective and what performing differences titan and neo4j have.

The most important bullets for any distributed database that come in our mind, are the following:

- Performance
- Scalability
- Backend Storage System
- Schema
- Indexing
- Search
- Modeling principles
- APIs

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


# Evaluation
Stay tuned for our grah database beanchmarking, which can describe with a distinctive view the performing results between Neo4j and Tinan Graph databases.
