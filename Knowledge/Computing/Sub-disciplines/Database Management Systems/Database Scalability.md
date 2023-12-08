# Database Scalability
**Database scalability** is the ability of a [[Database|database]] to handle changing demands by adding/removing resources. Databases use a host of techniques to cope.

## Dimensions

Database [[Scalability|scalability]] has three basic dimensions: 
- amount of data
- volume of requests
- size of requests

### Vertical
Vertical database scaling implies that the database system can fully exploit maximally configured systems, including typically multiprocessors with large memories and vast storage capacity. Such systems are relatively simple to administer, but may offer reduced availability. However, any single computer has a maximum configuration. If workloads expand beyond that limit, the choices are either to migrate to a different, still larger system, or to rearchitect the system to achieve horizontal scalability.

### Horizontal
Horizontal database scaling involves adding more servers to work on a single workload. Most horizontally scalable systems come with functionality compromises. If an application requires more functionality, migration to a vertically scaled system may be preferable.