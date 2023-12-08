# Data Model
Data Model is the abstract modeling of the [[Data Type#^Data | data]] description, data semantics, and consistency constraints of the data. It provides the conceptual tools for describing the design of a [[Database | database]] at each level of data abstraction. Data models define how data is connected to each other and how they are processed and stored inside the system.

### Three perspectives
A data model *instance* may be one of three kinds according to ANSI in 1975:

1.  [[Conceptual data model]]: describes the semantics of a domain, being the scope of the model. For example, it may be a model of the interest area of an organization or industry. This consists of entity classes, representing kinds of things of significance in the domain, and relationship assertions about associations between pairs of entity classes. A conceptual schema specifies the kinds of facts or propositions that can be expressed using the model. In that sense, it defines the allowed expressions in an artificial 'language' with a scope that is limited by the scope of the model.
2.  [[Logical data model]]: describes the semantics, as represented by a particular data manipulation technology. This consists of descriptions of tables and columns, object oriented classes, and XML tags, among other things.
3.  [[Physical data model]]: describes the physical means by which data are stored. This is concerned with partitions, CPUs, tablespaces, and the like.