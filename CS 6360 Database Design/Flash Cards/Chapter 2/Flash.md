TARGET DECK: CS 6360

START
Basic
Front:
What is data abstractions? 
Back:
the suppression of details of data organization and storage, and the highlighting of the essential features for an improved understanding of the data.
Tags:
Data Abstraction
<!--ID: 1724873939280-->
END

START
Basic
Front:
What is a relationship among two or more entities? 
Back:
Represents an association among the entities, for example, a works on relationship between an employee and a project. 
Tags:
Relationships
<!--ID: 1724873939286-->
END

START
Basic
Front:
What do physical data models decribe?
Back:
How data is stored as files in the computer by representing information such as record formats, record orderings, and access paths. 
Tags:
Abstraction
<!--ID: 1724873939289-->
END

START
Basic
Front:
What is an access path?
Back:
A search structure that makes the search for particular database records efficient, such as indexing or hashing. 
Tags:
Definitions
<!--ID: 1724873939294-->
END

START
Basic
Front:
What is an index?
Back:
An examples of an access path that allows direct access to data using an index term or keyword. 
Tags:
Definitions
<!--ID: 1724873939297-->
END

START
Basic
Front:
What are self-describing data models?
Back:
Unlike traditional DBMS with schemas, with these the data describe themselves like with key-value stores and XML.
Tags:
Definitions
<!--ID: 1724873939301-->
END

START
Basic
Front:
what is the database schema?
Back:
The description of a database that is specified during database design and is not expected to change frequently. 
Tags:
Definitions
<!--ID: 1724873939305-->
END

START
Basic
Front:
What is a schema diagram?
Back:
A diagram that displays the schema, or the structure of each record type, but not the actual instances of records. 
Tags:
Definitions
<!--ID: 1724873939310-->
END

START
Basic
Front:
What is a schema construct?
Back:
Each object in the schema. 
Tags:
Definitions
<!--ID: 1724873939313-->
END

START
Basic
Front:
What is a database state or snapshot?
Back:
The data in the database at a particular moment in time. 
Tags:
Definitions
<!--ID: 1724873939317-->
END

START
Basic
Front:
What is a valid state?
Back:
A state that satisfies the structure and constraints specified in the schema. 
Tags:
Definitions
<!--ID: 1724873939321-->
END

START
Basic
Front:
What is the intension?
Back:
The schema is sometimes called the intension, and a database is called an extension of the schema.
Tags:
Definitions
<!--ID: 1724873939327-->
END

START
Basic
Front:
What is the meta-data of the database and where is it stored?
Back:
It is a description of the schema and constraints, stored in the catalog. 
Tags:
Definitions
<!--ID: 1724873939332-->
END

START
Basic
Front:
What is the Three-schema architecture?
Back:
It is proposed to help achieve and visualize 3 of the four characteristics of the database approach: 1) use of a catalog to store the database description so as to make it self-describing. 2) insulation of programs and data. 3) Support of multiple user views. 
Tags:
Three-schema architecture
<!--ID: 1724873939337-->
END

START
Basic
Front:
What are the levels of the three-schema architecture?
Back:
1. Internal level- describes the physical storage structure of the database. 
2. Conceptual level- describes the structure of the whole database for a community of users. Concentrates on describing entities, data types, relationships, user operations and constraints. 
3. External or view level- Each describes the part of the database that particular user group is interested in and hides the rest of the database from that user group. 
Tags:
Three-schema architecture
<!--ID: 1724873939344-->
END

START
Basic
Front:
What are mappings?
Back:
The processes of transforming requests and results between levels of architecture.
Tags:
Definitions
<!--ID: 1724873939348-->
END

START
Basic
Front:
What is data independence?
Back:
The capacity to change the schema at one level of a database system without having to change the schema at the next higher level. 
Tags:
Data Independence
<!--ID: 1724873939352-->
END

START
Basic
Front:
What is Logical Data Independence?
Back:
The capacity to change the conceptual schema without having to change external schemas or application programs. 
Tags:
Data Independence
<!--ID: 1724873939357-->
END

START
Basic
Front:
What is physical data independence?
Back:
The capacity to change the internal schema without having to change the conceptual schema. 
Tags:
Data Independence
<!--ID: 1724873939361-->
END

START
Basic
Front:
Why does data independence occur when changes are made?
Back:
Data independence occurs because when the schema is changed at some level, the schema at the next higher level remains unchanged; only the ***mapping*** between the two levels is changed. 
Tags:
Data Independence
<!--ID: 1724873939364-->
END

START
Basic
Front:
What is the data definition language?
Back:
The language used to define both schemas in DMBSs where no strict separation of levels is maintained. 
Tags:
Database Languages
<!--ID: 1724873939368-->
END

START
Basic
Front:
What is the Storage definition language?
Back:
In databases where there is strict separation between the conceptual and internal levels, the DDL is used to specify the conceptual schema only while the SDL is used to specify the internal schema. 
Tags:
Database Languages
<!--ID: 1724873939371-->
END

START
Basic
Front:
What is the view definition language?
Back:
The language used to specify user views and their mappings to the conceptual schema. 
Tags:
Database Languages
<!--ID: 1724873939376-->
END

START
Basic
Front:
What is the data manipulation language?
Back:
The language used for retrieval, insertion, deletion, and modification of the data. 
Tags:
Database Languages
<!--ID: 1724873939379-->
END

START
Basic
Front:
High-level DML vs Low-Level
Back:
High level DMLS have statements processed by a compiler into lower level, one statement can query a a whole set, also known as set-at-a-time. The low level must be written to loop through and query each record at a time. High-level query specifies which, low-level specifies how. 
Tags:
Database Languages
<!--ID: 1724873885882-->
END

START
Basic
Front:
What are the three implicit properties of a database?
Back:
1. Represents some aspect of the real world, sometimes called to UoD or miniworld. 
2. Is a logically coherent collection of data with some inherent meaning. 
3. is designed, built, and populated with data for a specific purpose.
Tags:
Database properties
<!--ID: 1724953407359-->
END

START
Basic
Front:
Query vs Transaction
Back:
A query causes some data to be retrieved; a transaction may cause some data to be read and some data to be written into the database. 
Tags:
Transactions
<!--ID: 1724953407366-->
END

START
Basic
Front:
What is a database system?
Back:
The database and DBMS software together. 
Tags:
Definitions
<!--ID: 1724953407370-->
END

START
Basic
Front:
What are the four characteristics of the database approach vs the file-processing approach?
Back:
1. Self-describing nature of a database system. 
2. Insulation between programs and data, and data abstraction. 
3. Support of multiple view of the data. 
4. Sharing of data and multiuser transaction processing. 
Tags:
Database characteristics
<!--ID: 1724953407375-->
END

START
Basic
Front:
What is a view? 
Back:
A view may be a subset of the database or it may contain virtual data that is derived from the database files but not explicitly stored. 
Tags:
Definitions
<!--ID: 1724953407379-->
END

START
Basic
Front:
What is the isolation property?
Back:
The isolation property ensures that each transaction appears to execute in isolation from other transactions, even though hundreds of transactions may be executing concurrently. 
Tags:
Definitions
<!--ID: 1724953407382-->
END

START
Basic
Front:
What is the atomicity property?
Back:
The atomicity property ensures that either all the database operations in a transaction are executed or none are. 
Tags:
Definitions
<!--ID: 1724953407385-->
END

START
Basic
Front:
What are three kinds of users who are actively interested in the contents of a database system?
Back:
1. Database Administrators
2. Database Designers
3. End Users
Tags:
Actors on the Scene
<!--ID: 1724953407389-->
END

START
Basic
Front:
What are the three responsibilities of a DBA?
Back:
1. Authorizing access to the database. 
2. Coordinating and monitoring use of the database. 
3. Acquiring and allocating resources for the database.
Tags:
Database Administrator
<!--ID: 1724953407394-->
END

START
Basic
Front:
What are four types of end users?
Back:
1. Casual End users- may occasionally access the database, but they may need different information each time. 
2. Naïve or Parametric end user- main job function revolves around constantly querying and updating the database, using standard types of queries and updates called canned transactions. 
3. Sophisticated End Users- engineers, scientists..
4. Standalone users-maintain personal databases using ready-made programs. 
Tags:
End Users
<!--ID: 1724953407399-->
END

START
Basic
Front:
What are the four most common database utilities available in a DBMS?
Back:
1. Loading Utility
2. Backup Utility 
3. Storage Reorganization Utility
4. Performance Monitoring Utility
Tags:
DBMS
<!--ID: 1725318455876-->
END

START
Basic
Front:
What are the two main types of basic DBMS architectures that were created on the client/server framework?
Back:
Two-tier and Three-tier
Tags:
Client/Server
<!--ID: 1725318455887-->
END

START
Basic
Front:
This standards allows client side programs to call the DBMS, as long as both client and server machines have the necessary software installed?
Back:
the open database connectivity
Tags:
Client/Server
<!--ID: 1725318455893-->
END

START
Basic
Front:
In a three tier client server architecture, what is the second tier called, and what does it do? 
Back:
It is called the middle tier or application server or webserver. it provides an intermediate layer between the client and the database server. 
Tags:
Client/Server
<!--ID: 1725318455898-->
END

START
Basic
Front:
What are the 8 data models that characterize a DBMS?
Back:
1. Relational
2. object
3. object-relational
4. NOSQL
5. key-value
6. hierarchical
7. network
8. other
Tags:
DBMS
<!--ID: 1725318455905-->
END

START
Basic
Front:
What are the five criterion used to classify a DBMS?
Back:
1. Data model
2. Number of Users
3. Number of sites over which the database is distributed.
4. Cost
5. Types of Access Paths
Tags:
DBMS
<!--ID: 1725318455910-->
END

START
Basic
Front:
Of the two types of data independence (see previous question), which is harder to achieve? Why?
Back:
Logical Independence is harder to achieve because it allows structural and constraint changes without affecting application programs which is a much stricter requirement.
Tags:
Data Independence
<!--ID: 1725321715682-->
END


