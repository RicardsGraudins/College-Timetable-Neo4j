# College-Timetable-Neo4j
This repository contains code and information for my third-year undergraduate project for the module **Graph Theory.**
The module is taught to undergraduate students at [GMIT](http://www.gmit.ie/) in the Department of Computer Science and Applied Physics.
The lecturer is [Ian McLoughlin](https://ianmcloughlin.github.io/).

#### Project Guidelines
> You are required to prototype a Neo4j database for use in a timetabling system for GMIT. The database should store information about student groups, classrooms, lecturers, and work hours – just like the current timetabling system in use at GMIT.

> The minimum standard for this project is a GitHub repository containing a write-up detailing the design of the database and how it should be used, and an example Neo4j database with this design. The document should clearly state what data needs to be stored in a timetabling system, and how that data is to be represented in your database. This means that you must clearly specify the design choices you have made as to what data are represented as nodes, relationships, labels, relationship types and properties. It should also specify and give examples of Cypher queries for adding, changing, retreiving and deleting data. Your example database should contain data from GMIT.

#### Neo4j Database
Neo4j is one of the world's leading open source graph database. It is completely developed using the Java language by Neo Technology.

Neo4j is:
* An open source
* Schema-free
* No SQL
* Graph Database

#### Graph Database
A graph database, also called a graph-oriented database, is a type of [NoSQL](https://en.wikipedia.org/wiki/NoSQL) database that uses [graph theory](https://en.wikipedia.org/wiki/Graph_theory) to store, map and query relationships.

A graph database is essentially a collection of nodes and edges. Each node represents an entity (such as a person or business) and each edge represents a connection or relationship between two nodes. Every node in a graph database is defined by a [unique identifier](https://en.wikipedia.org/wiki/Unique_identifier), a set of outgoing edges and/or incoming edges and a set of properties expressed as [key/value pairs](https://en.wikipedia.org/wiki/Attribute%E2%80%93value_pair). Each edge is defined by a unique identifier, a starting-place and/or ending-place node and a set of properties.  The mantra of graph database enthusiasts is "If you can whiteboard it, you can graph it." The same cannot be said for [relational database management systems](https://www.tutorialspoint.com/sql/sql-rdbms-concepts.htm) (RDBMS) used by SQL databases.

#### Comparison of RDBMS to Graph database:
##### Entity Relationship Diagram of Northrend
![ERD of Northwind](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/Northwind_diagram.jpg)
##### Simple Graph of Northwind
![Simple Graph of Northwind](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/northwind_graph_simple.png)
##### Sample Query of the Northwind
![Sample Query of Northwind](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/northwind_graph_sample.png)

#### SQL Pains
* Complex to model and store relationships
* Performance degrades with increases in data
* Queries get long and complex
* Maintenance is painful

#### Graph Gains
* Easy to model and store relationships
* Performance of relationship traversal remains constant with growth in data size
* Queries are shortened and more readable
* Adding additional properties and relationships can be done on the fly - no migrations

#### Cypher Query Language
Neo4j uses [Cypher Query Language](https://en.wikipedia.org/wiki/Cypher_Query_Language) which is a relatively simple language, however it can preform queries that would be very complex in SQL relatively easily.

![Express Complex Queries Easily with Cypher](https://image.slidesharecdn.com/neo4jatlantagraphtalk09082016-160921141445/95/introducing-neo4j-18-638.jpg?cb=1474467344)

#### Neo4j Use Cases:
* Real Time Recommendations
* Master Data Management
* Fraud Detection
* Graph Based Search
* Network & IT-Operations
* Identity & Access Management

**Several examples of firms that utilize graphs and where:**
* Amazon - Related products feature
* Cisco - Consumer activity
* Lufthansa - Digital assets for in-flight entertainment system
* HP - Virtual machine management
* Facebook - Find a friend feature
* Blizzard Entertainment - Battle net client suggested friends feature

#### Installation Guide
1. Install Neo4j https://neo4j.com/download/
2. Download and unzip the project
3. Launch Neo4j and select the database location of the project

#### References
[Intro to Neo4j](https://www.youtube.com/watch?v=Yzbk6VaavoM)
[Northwind Introduction](https://neo4j.com/developer/guide-importing-data-and-etl/)
[Neo4j Overview](https://www.tutorialspoint.com/neo4j/neo4j_overview.htm)
