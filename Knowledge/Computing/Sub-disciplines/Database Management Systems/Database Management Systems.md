# Database Management Systems
Database Management Systems is a software that enables the easy creation, access, and modification of [[Database | databases]] for efficient and effective database management.

**Usage:**
- **Data Definition:** It helps in the creation, modification, and removal of definitions that define the organization of data in the database. 
- **Data Update:** It helps in the insertion, modification, and deletion of the actual data in the database. 
- **Data Retrieval:** It helps in the retrieval of data from the database which can be used by applications for various purposes. 
- **User Administration:** It helps in registering and monitoring users, enforcing data security, monitoring performance, maintaining data integrity, dealing with concurrency control, and recovering information corrupted by unexpected failure.

## Characteristics
- **Real-world entity** − A modern DBMS is more realistic and uses real-world entities to design its architecture. It uses the behavior and attributes too. For example, a school database may use students as an entity and their age as an attribute.
- **Relation-based tables** − DBMS allows entities and relations among them to form tables. A user can understand the architecture of a database just by looking at the table names.
- **Isolation of data and application** − A database system is entirely different than its data. A database is an active entity, whereas data is said to be passive, on which the database works and organizes. DBMS also stores metadata, which is data about data, to ease its own process.
- **Less redundancy** − DBMS follows the rules of normalization, which splits a relation when any of its attributes is having redundancy in values. Normalization is a mathematically rich and scientific process that reduces data redundancy.
- **Consistency** − Consistency is a state where every relation in a database remains consistent. There exist methods and techniques, which can detect attempt of leaving database in inconsistent state. A DBMS can provide greater consistency as compared to earlier forms of data storing applications like file-processing systems.
- **Query Language** − DBMS is equipped with query language, which makes it more efficient to retrieve and manipulate data. A user can apply as many and as different filtering options as required to retrieve a set of data. Traditionally it was not possible where file-processing system was used.

## Advantages of DBMS
- **Controls database redundancy:** It can control data redundancy because it stores all the data in one single database file and that recorded data is placed in the database.
- **Data sharing:** In DBMS, the authorized users of an organization can share the data among multiple users.
- **Easily Maintenance:** It can be easily maintainable due to the centralized nature of the database system.
- **Reduce time:** It reduces development time and maintenance need.
- **Backup:** It provides backup and recovery subsystems which create automatic backup of data from [[Computer Hardware]] and [Computer Software] failures and restores the data if required.
- **Multi-user interface:** It provides different types of user interfaces like graphical user interfaces, application program interfaces

## Disadvantages of DBMS
- **Cost of Hardware and Software:** It requires a high speed of data processor and large memory size to run DBMS software.
- **Size:** It occupies a large space of disks and large memory to run them efficiently.
- **Complexity:** Database system creates additional complexity and requirements.
- **Higher impact of failure:** Failure is highly impacted the database because in most of the organization, all the data stored in a single database and if the database is damaged due to electric failure or database corruption then the data may be lost forever.

## Architecture
> A Database store a lots of critical information to access data quickly and securely. Hence it is important to select a correct Architecture for efficient data management.
### 3-tier Architecture
The design of a DBMS depends on its architecture. It can be *centralized* or *decentralized* or *hierarchical*. The architecture of a DBMS can be seen as either single tier or multi-tier. An n-tier architecture divides the whole system into related but independent **n** modules, which can be independently modified, altered, changed, or replaced.

Types of DBMS Architecture:
- 1- tier Architecture
- 2- tier Architecture
- 3- tier Architecture

**In 1-tier architecture**, the DBMS is the only entity where the user directly sits on the DBMS and uses it. Any changes done here will directly be done on the DBMS itself.
- Does not provide handy tools for end-users

**In 2-tier architecture**, then it must have an application through which the DBMS can be accessed. Programmers use 2-tier architecture where they access the DBMS by means of an application. Here the application tier is entirely independent of the database in terms of operation, design, and programming.
![[2-tier architecture.svg]]

**In 3-tier architecture:**, there is another layer between the client and the server. The client does not directly communicate with the server. Instead, it interacts with an application server which further communicates with the database system and then the query processing and transaction management takes place. This intermediate layer acts as a medium for the exchange of partially processed data between server and client. This type of architecture is used in the case of large web applications.
![[3-tier architecture.svg]]
**Advantages:**
- **Enhanced scalability** due to distributed deployment of application servers. Now, individual connections need not be made between client and server.
- **Data Integrity** is maintained. Since there is a middle layer between client and server, data corruption can be avoided/removed.
- **Security** is improved. This type of model prevents direct interaction of the client with the server thereby reducing access to unauthorized data.
**Disadvantages:**
Increased complexity of implementation and communication. It becomes difficult for this sort of interaction to take place due to the presence of middle layers.

### Data Abstraction and Data Independence
Database systems comprise complex data-structures. In order to make the system efficient in terms of retrieval of data, and reduce complexity in terms of usability of users, developers use abstraction i.e. hide irrelevant details from the users. This approach simplifies database design.

![[3-levels of Data Abstraction.svg]]

1. **Physical Level:** At the physical level, the information about the location of database objects in the data store is kept. Various users of DBMS are unaware of the locations of these objects. In simple terms, physical level of a database describes how the data is being stored in secondary storage devices like disks and tapes and also gives insights on additional storage details.
2. **Conceptual Level (Logical Level):** At conceptual level, data is represented in the form of various database tables.  Also referred as logical schema, it describes what kind of data is to be stored in the database.
3. **External Level:**  An external level specifies a view of the data in terms of conceptual level tables.  Each external level view is used to cater to the needs of a particular category of users. For Example, FACULTY of a university is interested in looking course details of students, STUDENTS are interested in looking at all details related to academics, accounts, courses and hostel details as well. So, different views can be generated for different users. The main focus of external level is data abstraction.

#### Data Independence
Data independence means a change of data at one level should not affect another level.
1. **Physical Data Independence:** Any change in the physical location of tables and indexes should not affect the conceptual level or external view of data.
2. **Conceptual Data Independence:** The data at conceptual level schema and external level schema must be independent. This means a change in conceptual schema should not affect external schema. e.g.; Adding or deleting attributes of a table should not affect the user’s view of the table. But this type of independence is difficult to achieve as compared to physical data independence because the changes in conceptual schema are reflected in the user’s view.

## Phases of database design
Database designing for a real-world application starts from capturing the requirements to physical implementation using DBMS software which consists of following steps shown below:

![[Phases of database design.svg]]

**Conceptual Design:** The requirements of database are captured using high level conceptual data model.
**Logical Design:** Logical Design represents data in the form of relational model. ER diagram produced in the conceptual design phase is used to convert the data into the Relational Model.
**Physical Design:** In physical design, data in relational model is implemented using commercial DBMS like Oracle, DB2.

## Types of DBMS

- [[Relational Database Management System]]