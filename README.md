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

#### Commit Summary
1. Setup - Created empty database "Timetable"
2. Added README & Neo4j Info
3. Added additional Neo4j Info
4. Added Department & Courses data
5. Added images folder
6. Added Info about commit 4
7. Updated README
8. Added Rooms, Days, TimeSlots Data
9. Added Info about commit 8

#### Timetable Database Data
The following is a list of data that is stored in this timetable database for GMIT:
* A list of departments
* A list of courses/programs offered by the departments
* A list of modules that the courses are broken into
* A list of students that are participating in a specific course
* A list of groups the students are divided into
* A list of rooms
* A list of weekdays
* A list of timeslots for every hour from 9am to 6pm

Neo4j stores data as nodes, relationships and properties. All of the above *lists* are implemented as nodes and are related to each other by relationships. The nodes and relationships also contain relevant property data e.g. courses have the property name and max_students.

#### 4. Department & Courses Data
The goal of this commit was to implement departments, courses, modules, groups and students as nodes and create logical relationships between them in such a way that it is easy for the person creating the timetable to understand how all the data is connected to each other and to be able to add extra data in the future to any section of the database without much complexity.

Here are all the steps and queries for this commit:
1. Create a new department node for Computer Science & Applied Physics.
> create (ee:Department { name: "Computer Science & Applied Physics"})
2. Create a new program node for Computing in Software Development L7 YR 3 Sem 6.
> create (ee:Program { name:"Computing in Software Development L7 YR 3 Sem 6" })
3. Create a relationship between the department and the program.
> match (a:Department),(b:Program) where a.name = "Computer Science & Applied Physics" and b.name = "Computing in Software Development L7 YR 3 Sem 6" create (a)-[r:Manages]->(b) 
4. Create a new module node for graph theory taught by Ian McLoughlin .
> create (ee:Module { name: "Graph Theory", Lecturer: "Ian McLoughlin" })
5. Create a relationship between the program and the module.
> match (a:Program),(b:Module) where a.name = "Computing in Software Development L7 YR 3 Sem 6" and b.name = "Graph Theory" create (a)-[r:Contains]->(b)
6. Instead of creating a new module and then a new relationship to the program one by one, the following query creates 5 module nodes and 5 relations to the program.
> match (ee:Program) where ee.name = "Computing in Software Development L7 YR 3 Sem 6" create (ab:Module { name: "Database Management Systems", Lecturer: "Deirdre O'Donovan"}), (cd:Module { name: "Mobile Applications Development 2", Lecturer: "Damian Costello"}), (ef:Module { name: "Software Testing", Lecturer: "Martin Hynes"}), (gh:Module { name: "Server Side Rad", Lecturer: "Gerard Harrison"}), (ij:Module { name: "Professional Practice In IT", Lecturer: "Damian Costello"}), (ee)-[:Contains]->(ab), (ee)-[:Contains]->(cd), (ee)-[:Contains]->(ef), (ee)-[:Contains]->(gh), (ee)-[:Contains]->(ij)
7. Create a new node students that are participating in this program with a max number of students at 90.
> create (ee:Students { accepted_into: "Computing in Software Development L7 YR 3 Sem 6", max_students: "90"})
8. Similarily to step 6, create 3 group nodes A,B and C that have a max number of students at 30 each, also a relationship to students representing the students participating in the program are divided into 3 groups.
> match (ee:Students) where ee.accepted_into = "Computing in Software Development L7 YR 3 Sem 6" create (ab:Group { name: "A", course: "Computing in Software Development L7 YR 3 Sem 6", max_students: "30"}), (cd:Group { name: "B", course: "Computing in Software Development L7 YR 3 Sem 6", max_students: "30"}), (ef:Group { name: "C", course: "Computing in Software Development L7 YR 3 Sem 6", max_students: "30"}), (ee)-[:Divided_into]->(ab), (ee)-[:Divided_into]->(cd), (ee)-[:Divided_into]->(ef)

At this point the database should look like this: 
![Commit4_1](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Images/Commit4_1.png)

9. Create 2 student nodes with properties name, ID and age that are a part of group A.
> match (ee:Group) where ee.name = "A" create (ab:Student { name: "Ricards Graudins", age: "22", ID: "G00000000" }), (cd:Student { name: "John Johnson", age: "25", ID: "G00000001" }), (ee)-[:Composed_of]->(ab), (ee)-[:Composed_of]->(cd)
10. Last step is to create a relationship between the modules and the groups, in this case every module is taught to groups A,B and C.
> match (ee:Group),(m0:Module),(m1:Module),(m2:Module),(m3:Module),(m4:Module),(m5:Module) where ee.name = "A" and m0.name = "Graph Theory" and m1.name = "Software Testing" and m2.name = "Mobile Applications Development 2" and m3.name = "Database Management Systems" and m4.name = "Server Side Rad" and m5.name = "Professional Practice In IT" create (m0)-[:Taught_to]->(ee), (m1)-[:Taught_to]->(ee), (m2)-[:Taught_to]->(ee), (m3)-[:Taught_to]->(ee), (m4)-[:Taught_to]->(ee), (m5)-[:Taught_to]->(ee)

> match (ee:Group),(m0:Module),(m1:Module),(m2:Module),(m3:Module),(m4:Module),(m5:Module) where ee.name = "B" and m0.name = "Graph Theory" and m1.name = "Software Testing" and m2.name = "Mobile Applications Development 2" and m3.name = "Database Management Systems" and m4.name = "Server Side Rad" and m5.name = "Professional Practice In IT" create (m0)-[:Taught_to]->(ee), (m1)-[:Taught_to]->(ee), (m2)-[:Taught_to]->(ee), (m3)-[:Taught_to]->(ee), (m4)-[:Taught_to]->(ee), (m5)-[:Taught_to]->(ee)

> match (ee:Group),(m0:Module),(m1:Module),(m2:Module),(m3:Module),(m4:Module),(m5:Module) where ee.name = "C" and m0.name = "Graph Theory" and m1.name = "Software Testing" and m2.name = "Mobile Applications Development 2" and m3.name = "Database Management Systems" and m4.name = "Server Side Rad" and m5.name = "Professional Practice In IT" create (m0)-[:Taught_to]->(ee), (m1)-[:Taught_to]->(ee), (m2)-[:Taught_to]->(ee), (m3)-[:Taught_to]->(ee), (m4)-[:Taught_to]->(ee), (m5)-[:Taught_to]->(ee)

Now the database should look like this:
![Commit4_1](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Images/Commit4_2.png)

#### Useful Queries:
1. Displays all group nodes(and graph theory node) that are taught the graph theory module.
> match (ee:Module)-[:Taught_to]-(Group) where ee.name = "Graph Theory" return ee, Group
![Commit4_1](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Images/Commit4_3.png)

2. Displays students node and group nodes that have the relationship "Divided_into".
- Can easily see how many groups the students who got accepted into a specific course are divided into.
> match (ee:Students)-[Divided_into]-(Group) return ee, Group
![Commit4_1](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Images/Commit4_4.png)
- The proper way to do this query is:
> match (ee:Students)-[Divided_into]-(Group) where ee.accepted_into = "Computing in Software Development L7 YR 3 Sem 6" return ee, Group
- Both queries work however, the 2nd one should be used as the finished timetable will consist of several nodes called Students and they are seperated by the property accepted_into. In other words if the first query is used in a timetable that consists of several nodes called Students all of the Students nodes will be displayed and not just the ones for Computing in Software Development L7 YR 3 Sem 6.

3. Displays all module and group nodes and their relationships.
> match (ee:Module)-[]-(Group) return ee, Group

4. Displays group node and student nodes that have the relationship "Composed_of".
> match (ee:Group)-[:Composed_of]-(Student) return ee, Student

#### 8. Rooms, Days, TimeSlot Data
The goal of this commit was to add rooms, display the days and time slots the rooms are available, and lastly to create a relationship between the group occupying the room during a timeslot as well as the module being taught.

Here are all the steps and queries for this commit:
Several queries are inside a [seperate folder](https://github.com/RicardsGraudins/College-Timetable-Neo4j/tree/master/Cypher%20Queries) as they are too long for the README.

1. Create a new facility node for rooms.
> create (ee:Facility { name: "Rooms"})
2. Create 3 new activity nodes for lectures, computer labs and science labs.
> create (ee:Activity { name: "Lectures"}), (a:Activity { name: "Computer Labs"}), (b:Activity { name: "Science Labs"})
3. Create a relationship between the facility and 3 activities to represent what the facility is used for.
> match (ee:Facility),(a:Activity),(b:Activity), (c:Activity) where ee.name = "Rooms" and a.name = "Lectures" and b.name = "Computer Labs" and c.name = "Science Labs" create (ee)-[:For]->(a), (ee)-[:For]->(b), (ee)-[:For]->(c)
4. Create new room nodes with the property number.
> create (a:Room {number: "0145"}), (b:Room {number: "0994"}), (c:Room {number: "0223"}), (d:Room {number: "0481", ID: "CR4"}), (e:Room {number: "0436", ID: "CR5"}), (f:Room {number: "0470"}), (g:Room {number: "0379"}), (h:Room {number: "0162"}), (i:Room {number: "0938"}), (j:Room {number: "0208"}), (k:Room {number: "0997"}), (l:Room {number: "0939"}), (m:Room {number: "0995"}), (n:Room {number: "0483", ID: "CR2"}), (o:Room {number: "PF18"}),(p:Room {number: "0482", ID: "CR3"})
5. Create a relationship between activity "Computer Labs" and the 4 rooms that have computers to represent that the activity takes place in these 4 rooms.
> match (ee:Activity),(a:Room),(b:Room),(c:Room),(d:Room) where ee.name = "Computer Labs" and a.ID = "CR2" and b.ID = "CR3" and c.ID = "CR4" and d.ID = "CR5" create (ee)-[:In]->(a), (ee)-[:In]->(b), (ee)-[:In]->(c), (ee)-[:In]->(d)
6. Create a relationship between activity "Lectures" and the other rooms that are used for lectures.
> match (ee:Activity),(a:Room),(b:Room),(c:Room),(d:Room), (x:Room), (f:Room), (g:Room), (h:Room), (i:Room), (j:Room), (k:Room), (l:Room) where ee.name = "Lectures" and a.number = "0145" and b.number = "0994" and c.number = "0223" and d.number = "0470" and x.number = "0379" and f.number = "0162" and g.number = "0997" and h.number = "0938" and i.number = "0208" and j.number = "0995" and k.number = "0939" and l.number = "PF18" create (ee)-[:In]->(a), (ee)-[:In]->(b), (ee)-[:In]->(c), (ee)-[:In]->(d), (ee)-[:In]->(x), (ee)-[:In]->(f), (ee)-[:In]->(g), (ee)-[:In]->(h), (ee)-[:In]->(i), (ee)-[:In]->(j), (ee)-[:In]->(k), (ee)-[:In]->(l)

Screenshot match (ee:Facility)-[]-(Activity)-[]-(Room) return ee, Activity, Room
Science Labs is excluded because it is not connected to any rooms at the moment.
![Commit6_1.png](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Images/Commit6_1.png)

The next part involves creating Mon-Fri nodes for every room(80 nodes) and time slot nodes for every hour session 9am-6pm for every day of every room (720 nodes). The design plan/ideal-scenario for this project was to have only 5 Mon-Fri nodes and 9 time slot nodes which have relationships between them in such a way that only a minimum amount of nodes is needed to display that a certain group is occupying a certain room at a certain time slot for a certain module however that plan backfired and I decided to take an alternative approach. The flaw with this alternative approach is the fact that a high number of nodes must be created which means the database is going to need more storage space but as a result you end up with a database that clearly displays which room, day and timeslot is/isn't occupied by a group.

7. Create day nodes Mon-Fri with property room ID.
> Ref: [seperate folder](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Cypher%20Queries/Create%20Days.txt)
8. Create relationships between room nodes and day nodes, this is where the room ID property of day nodes is used.
> Ref: [seperate folder](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Cypher%20Queries/Relationships%20-%20Rooms%20and%20Days.txt)

Screenshot match (ee:Room)-[]-(Day)-[]-(TimeSlot) return ee, Day, TimeSlot
![Commit6_2.png](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Images/Commit6_2.png)

9. Create time slot nodes for every day of every room with property room ID.
> Ref: [seperate folder](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Cypher%20Queries/Create%20TimeSlots.txt)
10. Create relationships between day nodes and time slots, this is where the room ID property of time slot nodes is used.
> Ref: [seperate folder](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Cypher%20Queries/Relationships%20-%20Days%20and%20TimeSlots.txt)

Screenshot match (ee:Room)-[]-(Day)-[]-(TimeSlot) return ee, Day, TimeSlot
At this point there is a lot of nodes and only 300 is displayed unless :config initialNodeDisplay: 300 is modified.
![Commit6_3.png](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Images/Commit6_3.png)

11. Lastly create relationships between time slot nodes and group nodes representing that a time slot is occupied by a certain group and create relationships between module nodes and time slot nodes representing that a particular module is taught at a particular time slot. All the data for this part is completed acording to the timetable [here](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Images/Timetable.png)
> Ref: [seperate folder](https://github.com/RicardsGraudins/College-Timetable-Neo4j/blob/master/Cypher%20Queries/Relationships%20-%20Groups%2C%20Modules%2C%20TimeSlots.txt)
