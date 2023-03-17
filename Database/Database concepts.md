#### Schema
``` 
The database schema is the structure of a database described in a formal language supported by the database management system
(DBMS). The term "schema" refers to the organization of data as a blueprint of how the database is constructed (divided into
database tables in the case of relational databases). The formal definition of a database schema is a set of formulas (sentences)
called integrity constraints imposed on a database.[citation needed] These integrity constraints ensure compatibility between parts
of the schema. All constraints are expressible in the same language. A database can be considered a structure in realization of the
database language.[1] The states of a created conceptual schema are transformed into an explicit mapping, the database schema. This
describes how real-world entities are modeled in the database.
```
#### Cursor
```
In computer science, a database cursor is a mechanism that enables traversal over the records in a database. Cursors facilitate
subsequent processing in conjunction with the traversal, such as retrieval, addition and removal of database records. The database
cursor characteristic of traversal makes cursors akin to the programming language concept of iterator.

Cursors are used by database programmers to process individual rows returned by database system queries. Cursors enable 
manipulation of whole result sets at once. In this scenario, a cursor enables the sequential processing of rows in a result set.
```

#### Database view
```
In a database, a view is the result set of a stored query on the data, which the database users can query just as they would in a
persistent database collection object. This pre-established query command is kept in the database dictionary. Unlike ordinary base
tables in a relational database, a view does not form part of the physical schema: as a result set, it is a virtual table computed
or collated dynamically from data in the database when access to that view is requested. Changes applied to the data in a relevant
underlying table are reflected in the data shown in subsequent invocations of the view. In some NoSQL databases, views are the 
only way to query data.
```

#### Tablespace
```
A tablespace is a storage location where the actual data underlying database objects can be kept. It provides a layer of 
abstraction between physical and logical data,[1] and serves to allocate storage for all DBMS managed segments. (A database 
segment is a database object which occupies physical space such as table data and indexes.) Once created, a tablespace can be 
referred to by name when creating database segments.

Oracle stores data logically in tablespaces and physically in datafiles associated with the corresponding tablespace.
```

#### Sharding (One kind of partitioning, horizontal partition)
```
A database shard, or simply a shard, is a horizontal partition of data in a database or search engine. Each shard is held on a 
separate database server instance, to spread load.

Some data within a database remains present in all shards,[a] but some appear only in a single shard. Each shard (or server) acts 
as the single source for this subset of data.[1]
```

[Partition and shard](https://www.singlestore.com/blog/database-sharding-vs-partitioning-whats-the-difference/)

#### Partitioning
```
A partition is a division of a logical database or its constituent elements into distinct independent parts. Database partitioning
is normally done for manageability, performance or availability[1] reasons, or for load balancing. It is popular in distributed 
database management systems, where each partition may be spread over multiple nodes, with users at the node performing local 
transactions on the partition. This increases performance for sites that have regular transactions involving certain views of 
data, whilst maintaining availability and security.
```
