# Entity-Relational Model
The ER model defines the [[Data Model|conceptual view]] of a database. It works around real-world entities and the associations among them. At view level, the ER model is considered a good option for designing [[Database | databases]].

## Entity
An entity can be a real-world object, either animate or inanimate, that can be easily identifiable.
**In Crow's Foot Notation:**
![[Entity.svg]]
**In Chen's Notation:**
1. Entity ![[Entiry.svg]]
2. **Weak Entity** an entity that cannot be uniquely identified by its attributes alone.![[Weak Entity.svg]]
3. **Associative Entity** – an entity used in a many-to-many relationship (represents an extra table).![[Associative Entity.svg]]

## Attributes
Entities are represented by means of their properties, called **attributes**.

**In Crow's Foot Notation:**
![[Attributes.svg]]

**In Chen's Notation:**
Types of Attributes
- **Simple attribute** − Simple attributes are atomic values, which cannot be divided further. ![[Attribute.svg]]
- **Composite attribute** − Composite attributes are made of more than one simple attribute. ![[Composite Attribute.svg]]
- **Derived attribute** − Derived attributes are the attributes that do not exist in the physical database, but their values are derived from other attributes present in the database. ![[Derived Attribute.svg]]
- **Single-value attribute** − Single-value attributes contain single value. 
- **Multi-value attribute** − Multi-value attributes may contain more than one values.![[Multi-value Attribute.svg]]

## Entity-Set and Key
Key is an attribute or collection of attributes that uniquely identifies an entity among set of entities.![[Entity Set.svg]]![[Key Attribute.svg]]
- **Super Key** − A set of attributes (one or more) that collectively identifies an entity in an entity set.
- **Candidate Key** − A minimal super key is called a candidate key. An entity set may have more than one candidate key.
- **Primary Key** − A primary key is one of the candidate keys chosen by the database designer to uniquely identify the entity set.
- **Foreign Key** − A foreign keys are the column of the table used to point to the primary key of another entity.

## Relationship
The logical association among entities is called a relationship. 

### Relationship Set
A set of relationships of similar type is called a relationship set. Like entities, a relationship too can have attributes. These attributes are called **descriptive attributes**.

### Degree of Relationship
The number of participating entities in a relationship defines the degree of the relationship.
-   Binary = degree 2
-   Ternary = degree 3
-   n-ary = degree n

### Mapping Cardinalities
**Cardinality** defines the number of entities in one entity set, which can be associated with the number of entities of other set via relationship set.
- **One-to-one** − One entity from entity set A can be associated with at most one entity of entity set B and vice versa. 
- **One-to-many** − One entity from entity set A can be associated with more than one entities of entity set B however an entity from entity set B, can be associated with at most one entity.
- **Many-to-one** − More than one entities from entity set A can be associated with at most one entity of entity set B, however an entity from entity set B can be associated with more than one entity from entity set A.
- **Many-to-many** − One entity from A can be associated with more than one entity from B and vice versa.

### In Chen's Notation:
**Relationship:**
1. **Strong relationship** – a relationship where entity is existence-independent of other entities, and PK of Child doesn’t contain PK component of Parent Entity. A strong relationship is represented by a single rhombus:![[Relationship.svg]]
2. **Weak (identifying) Relationship** – a relationship where Child entity is existence-dependent on parent, and PK of Child Entity contains PK component of Parent Entity. This relationship is represented by a double rhombus:![[Weak Relation.svg]]
Optionality of a relationship
1.  Similarly to the Barker’s notation, a **mandatory** relationship is represented by a solid line:![[Mandatory  Relation.svg]]
2.  An **optional** relationship is represented by a dashed line like in Barker’s notation:![[Optional Relationship.svg]]

**Relation Set:**
![[Relation Set.svg]]

**Cordinality:**
![[Chen's Cordinality.svg]]

#### Participation constraints
An entity set may participate in a relation either totally or partially.
- **Total participation** means that every entity in the set is involved in the relationship, e.g., each student must be guided by a professor (there are no students who are not guided by any professor). In the Chen notation, this kind of relation is depicted as a double line.
- **Partial participation** means that not all entities in the set are involved in the relationship, e.g., not every professor guides a student (there are professors who don’t). In the Chen notation, a partial participation is represented by a single line.
![](https://vertabelo.com/blog/chen-erd-notation/chen-notation-participation-constraints.png)

### In Crow's Foot Notation:
**Relationship:**
Relationships are presented as a straight line.  Usually, each relationship has a name, expressed as a verb, written on the relationship line. This describes what kind of relationship connects the objects.

**Cordinality:**
Relationships have two indicators. These are shown on both sides of the line.
- The first one (often called **multiplicity**) refers to the _maximum_ number of times that an instance of one entity can be associated with instances in the related entity. It can be **one** or **many**.
  ![Multiplicity of one in crow’s foot notation](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-multiplicity-of-one.png)
  ![Multiplicity of many in crow’s foot notation](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-multiplicity-of-many.png)
- The second describes the _minimum_ number of times one instance can be related to others. It can be **zero** or **one**, and accordingly describes the relationship as **optional** or **mandatory**.
  ![Mandatory relationship in crow’s foot notation](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-mandatory.png)
  ![Optional relationship in crow’s foot notation](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-optional.png)

The combination of these two indicators is always in a specific order. Placed on the outside edge of the relationship, the symbol of multiplicity comes first. The symbol indicating whether the relationship is mandatory or optional is shown after the symbol of multiplicity.

In crow’s foot notation:

- A multiplicity of **one** and a **mandatory relationship** is represented by a straight line perpendicular to the relationship line.
- A multiplicity of **many** is represented by the three-pronged ‘crow-foot’ symbol.
- An **optional relationship** is represented by an empty circle.

- zero or many
  ![Zero or many relationship in crow’s foot notation](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-zero-or-many.png)
- one or many
  ![One or many relationship in crow’s foot notation](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-one-or-many.png)
- one and only one
  ![One and only one relationship in crow’s foot notation](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-one.png)
- zero or one
  ![Zero or one relationship in crow’s foot notation](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-one-or-zero.png)
    
**Examples**
Relationship degrees make them readable as :
- One-to-one
  ![One-to-one](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-one-to-one.png)
- One-to-many
  ![One-to-many](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-one-to-many.png)
- Many-to-many
  ![Many-to-many](https://vertabelo.com/blog/crow-s-foot-notation/crows-foot-notation-many-to-many.png)

## Generalization
 In generalization, a number of entities are brought together into one generalized entity based on their similar characteristics.![[Pasted image 20220911155729.png]]
## Specialization
Specialization is the opposite of generalization. In specialization, a group of entities is divided into sub-groups based on their characteristics.![[Pasted image 20220911155733.png]]
## Inheritance
Inheritance is an important feature of Generalization and Specialization. It allows lower-level entities to inherit the attributes of higher-level entities.![[Pasted image 20220911155736.png]]