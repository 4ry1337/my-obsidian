# Graph Database
A **graph database** (**GDB**) is a [[Database|database]] that uses [[Graph|graph structures]] for semantic queries with nodes, edges, and properties to represent and store data.

## Properties
Graph databases are a powerful tool for graph-like queries. For example, computing the shortest path between two nodes in the graph. Other graph-like queries can be performed over a graph database in a natural way (for example graph's diameter computations or community detection).

Graphs are flexible, meaning it allows the user to insert new data into the existing graph without loss of application functionality. There is no need for the designer of the database to plan out extensive details of the database's future use cases.

### Storage
The underlying storage mechanism of graph databases can vary. Some depend on a relational engine and "store" the graph data in a table (although a table is a logical element, therefore this approach imposes another level of abstraction between the graph database, the graph database management system and the physical devices where the data is actually stored). Others use a [[Key-Value Database|key–value store]] or [[Document-Oriented Database|document-oriented database]] for storage, making them inherently [[NoSQL Database|NoSQL]] structures. A node would be represented as any other document store, but edges that link two different nodes hold special attributes inside its document; a _from and _to attributes.

### Graph types
There are multiple types of graphs that can be categorized. Gartner suggests the five broad categories of graphs:[[Gartner]](https://en.wikipedia.org/wiki/Graph_database#cite_note-17)
- Social graph: this is about the connections between people;
- Intent graph: this deals with reasoning and motivation.
- Consumption graph: also known as the "payment graph", the consumption graph is heavily used in the retail industry. E-commerce companies such as Amazon, eBay and Walmart use consumption graphs to track the consumption of individual customers.
- Interest graph: this maps a person's interests and is often complemented by a social graph. It has the potential to follow the previous revolution of web organization by mapping the web by interest rather than indexing webpages.
- Mobile graph: this is built from mobile data. Mobile data in the future may include data from the web, applications, digital wallets, GPS, and Internet of Things (IoT) devices.