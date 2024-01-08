# Document-Oriented Database
A **document-oriented database**, or **document store**, is a data storage system designed for storing, retrieving and managing document-oriented information, also known as semi-structured data.

The central concept of a document-oriented database is the notion of a *document*. While each document-oriented database implementation differs on the details of this definition, in general, they all assume documents encapsulate and encode data (or information) in some standard format or encoding. Encodings in use include [[XML]], [[YAML]], [[JSON]], as well as binary forms like [[BSON]].

Documents are addressed in the database via a unique *key* that represents that document. Another defining characteristic of a document-oriented database is an API or query language to retrieve documents based on their contents.

Different implementations offer different ways of organizing and/or grouping documents:

- Collections
- Tags
- Non-visible metadata
- Directory hierarchies

Compared to relational databases, collections could be considered analogous to tables and documents analogous to records. But they are different: every record in a table has the same sequence of fields, while documents in a collection may have fields that are completely different.