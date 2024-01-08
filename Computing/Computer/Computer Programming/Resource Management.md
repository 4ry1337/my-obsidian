# Resource Management
In [[Computer Programming|computer programming]], **resource management** refers to techniques for managing resources.

Host-based management is known as *resource tracking*, and consists of clean up resource leaks: terminating access to resources that have been acquired but not released after user. This is known as *reclaiming resources*m and is analogous to [[Garbage Collection|garbage collection]] for memory.

## Control Access

The omission of releasing a  resource when a program has finished using it is known as a [[Resource Leak|resource leak]], and is an issue in sequential computing, 

Multiple processes with to access a limited resource can be an issue in [[Concurrent Computing|concurrent computing]], and is known as [[Resource Contention|resource contention]]

Resource management seeks to control access in order to prevent both of these situations.